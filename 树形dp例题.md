~~~
include <iostream>

include <cstdio>

include <cstring>

include <algorithm>

using namespace std;

int first[205];

int nex[205];

int v[205];

int w[205];

int eid;

int dp205;

void init()

{

    memset(dp,0,sizeof(dp));
    memset(w,0,sizeof(w));
    eid=0;
    for(int i=0;i<205;i++)
        first[i]=-1;

}

void addedge(int m,int n)

{

    v[++eid]=n;
    nex[eid]=first[m];
    first[m]=eid;

}

void solve(int st,int sx)

{

    int i;
    dp[st][1]=w[st];
    for(i=first[st];i!=-1;i=nex[i])
    {
        int to=v[i];
        if(sx>1)
        solve(to,sx-1);
        for(int j=sx;j>=1;j--)
        {
            int v=j+1;
            for(int k=1;k<=j;k++)
                dp[st][v]=max(dp[st][v],dp[st][v-k]+dp[to][k]);
        }
    }

}

int main()

{

    int n,m;
    while(scanf("%d%d",&n,&m)!=EOF)
    {
        if(m==0&&n==0)
            break;
        init();
        int i;
        for(i=1;i<=n;i++)
        {
            int a,b;
            scanf("%d%d",&a,&b);
            addedge(a,i);
            w[i]=b;
        }
    
        solve(0,m+1);
        printf("%d\n",dp[0][m+1]);
    }
    return 0;

}

~~~

