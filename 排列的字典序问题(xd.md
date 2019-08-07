[题目链接](https://acm.sdut.edu.cn/onlinejudge2/index.php/Home/Contest/contestproblem/cid/2465/pid/1717)
![题目描述](http://wx2.sinaimg.cn/mw690/0060lm7Tly1fsnpoux7fxj30h90nkq49.jpg)


思路：

分两步：

一、计算字典值。

 我们可以从从开始算，因为不能有重复，以1开头的后面有7位数有1*7！，然后以2开头的后面有六位数，但第二位要小于6，即有1、3、4、5满足，有4*6！，然后以26...开头的后面有5位数，要求第三位要小于4，即有1，3满足，有2*5！，，，依次类推。。。
       

看例子：

tot=0；

比2小的数有1个，则 tot+=1*7！；

比6小的数有4个，则 tot+=4*6！；

比4小的数有2个，则 tot+=2*5！；

比5小的数有2个，则 tot+=2*4！；

比8小的数有3个，则 tot+=3*3！；

比1小的数有0个，则 tot+=0*2！；

比7小的数有1个，则 tot+=1*1！；

比3小的数没有；

（注：在排列中，求比某个数小的数的个数时，排除之前出现过的数）

 

二、下一个排列。



从数组最后找，找到一个比最后一个数小的数把最后一个数放在之前就可以了

 

可以用   next_permutation(order,order+n);   来求下一个排列，注意开头 加上 

#include<algorithm>
using namespace std;




```
#include<iostream>
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int jc[21];
    //先算阶乘
    jc[0]=1;
    for(int i=1;i<21;i++)
        jc[i]=jc[i-1]*i;
    
    int n,sum=0,*a,t;
    //n是多少个数，sum是字典序值，a是数组，t是比当前数小的数的个数

    while(cin>>n)
    {
        a=new int[n+1];
        for(int i=0;i<n;i++)//输入数据
            cin>>a[i];
        for(int i=0;i<n-1;i++)
        {
            t=a[i]-1;//比a[i]小的数最多有a[i]-1个
            //循环找前面，如果前面有比当前数小的数，后面比他小的数就少一个
            for(int j=0;j<=i;j++)
            {
                if(a[i]>a[j])
                    t--;
            }
            sum+=t*jc[n-i-1];//计算当前排列数，累加
        }
        cout<<sum<<endl;
        next_permutation(a,a+n);
        for(int i=0;i<n;i++)
            cout<<a[i]<<" ";
        cout<<endl;

    }
    return 0;

}
```