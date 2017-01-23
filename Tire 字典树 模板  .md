~~~
include<stdio.h>

include<string.h>

include<stdlib.h>

typedef struct node

{

    int cnt;
    struct node *next[26];

}*tree,t;

tree root;

void insert(char *str)

{

    tree p=root,newnode;
    for(;*str!='\0';str++)
    {
        if(p->next[*str-'a']!=NULL)
        {
            p=p->next[*str-'a'];
            p->cnt++;
        }
        else
        {
            newnode=(tree)malloc(sizeof(t));
          for(int i=0;i<26;i++)
            newnode->next[i]=NULL;
          newnode->cnt=1;
          p->next[*str-'a']=newnode;
          p=newnode;
        }
    }

}

int find(char *str)

{

    tree p=root;
    for(;*str!='\0';str++)
    {
        if(p->next[*str-'a']!=NULL)
        p=p->next[*str-'a'];
        else return 0;
    }
    return p->cnt;

}

int main()

{

    char str[16];
    root=(tree)malloc(sizeof(t));
    for(int i=0;i<26;i++)
        root->next[i]=NULL;
    root->cnt=0;//根节点初始化当然为0，不包含任何字母
    while(gets(str))
    {
        if(strcmp(str,"")==0)
            break;
        insert(str);
    }
    while(gets(str))
    {
        //if(strcmp(str,"")==0)
            //break;
        printf("%d\n",find(str));
    }
    return 0;

}

~~~

