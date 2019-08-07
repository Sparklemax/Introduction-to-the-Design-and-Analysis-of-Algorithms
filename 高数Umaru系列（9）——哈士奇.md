[题目链接](https://acm.sdut.edu.cn/onlinejudge2/index.php/Home/Contest/contestproblem/cid/2466/pid/3358)
![题目描述](http://wx3.sinaimg.cn/mw690/0060lm7Tly1fsoft7vuhaj30mi0nv75r.jpg)



```
#include <iostream>

using namespace std;

int main()
{
    int price[101];
    int cute[101];
    int n,money;
    while(cin>>n>>money)
    {
        int sum[10020]={0};
        for(int i=0;i<n;i++)
            cin>>price[i]>>cute[i];
        for(int i=0;i<n;i++)
        {
            for(int j=money;j>=price[i];j--)
            {
                if(sum[j]<sum[j-price[i]]+cute[i])
                    sum[j]=sum[j-price[i]]+cute[i];
            }
        }
        cout<<sum[money]<<endl;
    }
    return 0;
}
```