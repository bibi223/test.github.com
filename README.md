## Welcome to GitHub Pages 


# Header 1
## Header 2
### Header 3

#程序的优化陷阱
##memory aliasing(存储器别名使用)
eg:
void twiddle_1(int *xp,int *yp)
{
  *xp += *yp;
  *xp += *yp;
}
void twiddle_2(int *xp,int *yp)
{
  *xp += 2 * *yp;
}

f_1需要六次（读xp*2,读yp*2,写xp*2）存储器引用。
f_2需要3次（读xp,读yp,写xp）存储器引用。

所以我们可能会想让编译器将f_1优化成f_2的样子。但是如果遇到一下情况
