[题目链接](https://acm.sdut.edu.cn/onlinejudge2/index.php/Home/Contest/contestproblem/cid/2467/pid/1760)
![题目描述](http://wx3.sinaimg.cn/mw690/0060lm7Tly1fsqo97m8gij30mu0nmabg.jpg)


```
#include <bits/stdc++.h>
using namespace std;
typedef long long LL;
int n,k;
int x;
int main(){
    priority_queue<int>q;
    priority_queue<int,vector<int>,greater<int> >p;
    scanf("%d%d",&n,&k);
    for(int i=0;i<n;i++){
        scanf("%d",&x);
        q.push(x);
        p.push(x);
    }

    LL Max=0;
    while(q.size()>1){
        LL x=q.top();
        q.pop();
        LL y=q.top();
        q.pop();
        Max+=x+y;
        q.push(x+y);
    }

    while(p.size()%(k-1)!=1)p.push(0);
    LL Min=0;
    while(p.size()>1){
        if(k>p.size())
            k=p.size();
        LL sum=0;
        for(int i=0;i<k;i++){
            sum+=p.top();
            p.pop();
        }
        Min+=sum;
        p.push(sum);
    }
    printf("%lld %lld\n",Max,Min);
}


```