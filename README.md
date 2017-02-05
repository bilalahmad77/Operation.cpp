//# Operation.cpp It is a program written in c++ for link list. It is performing different operations on linked list.Compile and see the output.
#include<iostream.h>
class linklist
{
private:
struct node
{
int data;
node *link;
} *p;

public:

linklist();
void append(int num);
void addatbeg(int num);
void addafter(int loc,int num);
void display();
int count();
void del (int num);
~linklist();
};

linllist::linklist()
{
p=NULL;
}

void linklist::append(int num)
{
node *temp, *r;
if(p==NULL)
{
temp=new node;
temp -> data=num;
temp ->link=NULL;
}

else
{
temp=p;
while(temp -> link !=NULL)
temp=temp -> link;
r=new node;
r->data=num;
r->link=NULL;
temp -> link=r;
}
}

void linklist::addatbeg(int num)
{
node *temp;
temp=new node;
temp -> data=num;
temp -> link=p;
p=temp;
}

void linklist::addafter(int loc, int num)
{
node *temp, *r;
temp=p;
for (int i=0;i< loc ;i++)
{
temp=temp->link;
if(temp == NULL)
{
cout<<"\n There are less than"<< loc
<<"elements in list"<< endl;
return;
}
}
r=new node;
r -> data = num;
r -> link = temp -> link;
temp -> link=r;
}

void linklist::display()
{
node *temp = p;
cout << endl;
while(temp != NULL)
{
cout << temp -> data <<" ";
temp = temp -> link;
}
}

int  linklist::count()
{
node *temp=p;
int c=0;
while(temp != NULL)
{
temp = temp -> link;
c++;
}
return c;
}
void linklist::del(int num)
{
node *old, *temp;
temp = p;
while(temp != NULL)
{
if(temp -> data == num)
{
if (temp == p)
p = temp -> link;
else
old -> link = temp -> link;
delete temp;
return;
}
else
{
old = temp;
temp = temp -> link;
}
}
cout<<"\n\n No"<<num<<" element found";
}
linklist::~linkist()
{
node *q;
while(p != NULL)
{
q = p -> link;
delete p;
p = q;
}
}
void main()
{
linklist op;
op.append(15);
op.append(31);
op.append(26);
op.append(43);
op.append(18);
cout<<"\n Elements in the linked list:";
op.display();

op.addatbeg(666);
op.addatbeg(555);
op.addatbeg(333);

cout<<"\n Elements in the linked list after addition at the start:";
op.dispaly();
op.addafter(7,0);
op.addafter(2,1);
op.addafter(5,99);

cout<<"\n Elements in the linked list after addition at given position:";
op.dispaly();
cout<<"\n Total Elements found in the linked list:"<<op.count();

op.del(99);
op.del(1);
op.del(10);

cout<<"\n Elements in the linked list after deletion:";
op.dispaly();
cout<<"\n  Total Elements found in the linked list:"<<op.count();

}

