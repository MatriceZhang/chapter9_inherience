chapter9_inherience
===================


//
//  main.cpp
//  chapter 8
//
//  Created by zhangshiyu on 11/16/14.
//  Copyright (c) 2014 ZSY. All rights reserved.
//

#include<iostream>
using namespace std;


class Stack
{
protected:
    enum{MAX=3};  //size of stack arry
    int st[MAX];
    int top;   //index to top of stack
public:
    Stack()
    {top=-1;}
    void push(int var)  //put number on stack
    {st[++top]=var;}
    int pop()
    {return st[top--];}  //tale number off stack
    
};

class Stack2:public Stack
{
public:
    void push(int var)   //put number on stack
    {
        if(top>=MAX-1)  //error if stack full
        {cout<<"\nError:stack is full";exit(1);}
        Stack::push(var);   //call push() in stack class
        
    }
    int pop()
    {
        if(top<0)  //error if stack empty
        {cout<<"\nError:stack is empty\n";exit(1);}
        return Stack::pop();   //call pop() in stack class
    }
};


int main()
{
    Stack2 s1;
    s1.push(11);
    s1.push(22);
    s1.push(33);
    
    cout<<endl<<s1.pop();
    cout<<endl<<s1.pop();
    cout<<endl<<s1.pop();
    cout<<endl<<s1.pop();//opps,poped one too many..
    cout<<endl;
    return 0;
}

