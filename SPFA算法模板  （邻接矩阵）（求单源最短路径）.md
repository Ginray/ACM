~~~
include<iostream>

include<cstdio>

include<cstring>

include<cstdlib>

include<queue>

using namespace std;

define Max 9999999;

int a105;

int flag[105];//保存是否被访问过

int dis[105];//与节点0的最短路径的大小

int n;

queue<int> q;

void innt ()

{

memset(a,0,sizeof(a));

memset(flag,0,sizeof(flag));

dis[0]=0;

int i;

for(i=1;i<n;i++)

dis [i]=Max;

return ;

}

void SPFA (int s)//开始的节点

{

 q.push(s);

 while(!q.empty())

 {

 int x=q.front();

 flag[x]=1;

 int i;

 for(i=0;i<n;i++)

    {
       if(a[i][x]!=0&&(dis[x]+a[i][x])<dis[i])
       {
       dis[i]=dis[x]+a[i][x];
       if(!flag[i])
       {
       q.push(i);
       flag[i]=1;
       }
       }
    
    }

 q.pop();

 flag[x]=0;

 }

 return ;

}

int main ()

{

 while(scanf("%d",&n)!= EOF)

 {

 int i,j;

 int f;

 innt();//用矩阵来储存,

 for(i=1;i<n;i++)

 {

     for(j=0;j<i;j++)
     {
        scanf("%d",&f);
        a[i][j]=f;
        a[j][i]=f;
    
     }

 }

SPFA (0);

int minn=-1*Max;

 for(i=1;i<n;i++)

 {

 if(dis[i]>minn)

   minn=dis[i];

 }

 printf("%d\n",minn);

 }

return 0;

}



~~~

