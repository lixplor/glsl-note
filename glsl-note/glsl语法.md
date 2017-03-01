# OpenGL ES着色器语言语句

## 循环

### For循环

```c
for(;;) {}

for(int i = 0; i <= 99; i++) { aFunction(); }
```

* 关键字`for`用于描述一个由计数器控制的循环. 圆括号包裹三个表达式, 用于计数器的初始化, 检查, 和更新. 大括号定义的部分是每次循环执行的语句.
* 循环可以通过`continue`或`break`语句来跳过或终止

### While循环

```c
while() {}

while(i <= 99) { aFunction(); }
```

* 关键字`while`用于描述一个由条件控制的循环. 圆括号包裹条件表达式, 大括号定义了每次循环要执行的语句
* 循环可以通过`continue`或`break`语句来跳过或终止

### do while循环

```c
do {} while();

do { aFunction(); } while(i <= 99);
```

* 关键字`do`与`while`结合用于描述一个由条件控制的循环. 大括号定义了每次循环要执行的语句, 圆括号包裹条件表达式
* 循环可以通过`continue`或`break`语句来跳过或终止
* 与普通while循环不同, 即使do while循环的条件从最初就是false, 循环体也至少会执行一次

### 终止单次循环

```c
continue;
```

* 关键字`continue`用于退出单次循环. continue之后的所有语句都会被忽略, 然后立刻执行下一次循环

### 终止循环

```c
break;
```

* 关键字`break`用于在循环内终止整个循环. break后的所有语句都会被忽略, 循环会立刻退出


## 条件执行

### if语句

```c
if() {}

if(i != 0) { aFunction(); }
```

* 关键字`if`用于描述语句执行的条件. 圆括号包裹定义的条件, 大括号包裹当条件为true时要执行的语句
* 与循环不同, 大括号的内容只执行一次, 或根本不执行

### else语句

```c
if() {} else {}

if(i != 0) { aFunction(); } else { bFunction(); }
```

* 关键字`else`结合if用于描述语句的备选条件.


## 退出执行

### return语句

```c
return;

return aValue;
```

* 关键字`return`用于定义合适的退出函数的方法.

### discard语句

```c
discard;
```

* 关键字`discard`用于为fragemnt shader定义一个异常的退出. 它用于立刻退出fragemnt shader, 并告知OpenGL ES 2.0管道相应的fragment不再需要绘制


## 开始执行

### main方法

```c
void main(void) {}
```

* 关键字`main`用于定义shader的主函数. 该函数是每个vertex和fragment shader的执行入口. main函数不需要参数, 也不返回任何值
