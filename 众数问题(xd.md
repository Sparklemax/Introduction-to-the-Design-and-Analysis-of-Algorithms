[题目链接](https://acm.sdut.edu.cn/onlinejudge2/index.php/Home/Contest/contestproblem/cid/2465/pid/1710.html)

![题目描述](http://wx2.sinaimg.cn/mw690/0060lm7Tly1fsnongq5saj30ks0kojs7.jpg)

```
#include <iostream>
#include <algorithm>

using namespace std;

int main()
{
    int n,i,*a;
    int num,count=0,maxcount=0,max;

    scanf("%d",&n);
    a=new int[n];

    for(i=0;i<n;i++)
        scanf("%d",&a[i]);

    sort(a,a+n);

    for(i=0;i<n;i++)
    {
        if(num!=a[i])
            count=1;
        else
            count++;
        num=a[i];
        if(count>maxcount)
        {
            max=num;
            maxcount=count;
        }
    }
    printf("%d\n%d\n",max,maxcount);

    return 0;
}


```