**singly linked list**
#include<iostream>
#include<cstdlib>
using namespace std;
struct node
{
	int info;
	struct node *next;
}*start;
class single_list
{
	public:
		node*create_node(int);
		void insert_begin();
		void insert_last();
		void insert_pos();
		void delete_pos();
		void delete_begin();
		void delete_last();
		void update_begin();
		void update_last();
		void update_pos();
		void sort();
		void reverse();
		void search();
		void display();
		single_list()
		{
			start=NULL;
		}
};
int main()
{
	int choice;
	single_list s1,s2;
	start=NULL;
	do
	{
		cout<<"----------"<<endl;
		cout<<"operations on singly linked list"<<endl;
		cout<<"--------------------------"<<endl;
		cout<<"1.insert at first"<<endl;
		cout<<"2.insert at last"<<endl;
		cout<<"3.insert at position"<<endl;
		cout<<"4.delete at first"<<endl;
		cout<<"5.delete at last"<<endl;
		cout<<"6.delete at position"<<endl;
		cout<<"7.update at first"<<endl;
		cout<<"8.update at last"<<endl;
		cout<<"9.update at position"<<endl;
		cout<<"10.ascending order"<<endl;
		cout<<"11.descending order"<<endl;
		cout<<"12.search"<<endl;
		cout<<"13.display"<<endl;
		cout<<"14.exit"<<endl;
		cout<<"enter your choice:";
		cin>>choice;
		switch(choice)
		{
			case 1:s1.insert_begin();
			s1.display();
			break;
			case 2:s1.insert_last();
			s1.display();
			break;
			case 3:s1.insert_pos();
			s1.display();
			break;
			case 4:s2.delete_begin();
			s1.display();
			break;
			case 5:s2.delete_last();
			s1.display();
			break;
			case 6:s1.delete_pos();
			s1.display();
			break;
			case 7:s1.update_begin();
			s1.display();
			break;
			case 8:s1.update_last();
			s1.display();
			break;
			case 9:s1.update_pos();
			s1.display();
			break;
			case 10:s1.sort();
			s1.display();
			break;
			case 11:s1.reverse();
			s1.display();
			break;
			case 12:s1.search();
			s1.display();
			break;
			case 13:s1.display();
			break;
			case 14:exit(0);
			break;
			default:cout<<"wrong choice...???"<<endl;
			break;
		}
	}
	while(choice!=14);
}
node *single_list::create_node(int value)
{
	struct node *temp,*s;
	temp=new(struct node);
	if(temp==NULL)
	{
		cout<<"memory not allocated"<<endl;
		return 0;
	}
	else
	{
		temp->info=value;
		temp->next=NULL;
		return temp;
	}
}
void single_list::insert_begin()
{
	int value;
	cout<<"enter the value to be inserted:";
	cin>>value;
	struct node *temp,*s;
	temp=create_node(value);
	if(start==NULL)
	{
		start=temp;
		start->next=NULL;
		cout<<temp->info<<"is inserted at first in the empty list"<<endl;
	
	}
	else
	{
		s=start;
		start=temp;
		start->next=s;
		cout<<temp->info<<"is inserted at first"<<endl;
		
	}
			}
			void single_list::insert_last()	
			{
				int value;
				cout<<"enter the value to be inserted:";
				cin>>value;
				struct node *temp,*s;
				temp=create_node(value);
				if(start==NULL)
				{
					start=temp;
					start->next=NULL;
					cout<<temp->info<<"is inserted at last in the empty list"<<endl;
					
				}
				else
				{
					s=start;
					while(s->next!=NULL)
					{
					
					s=s->next;
					}
					temp->next=NULL;
					s->next=temp;
					cout<<temp->info<<"is inserted at last"<<endl;
				}
					}
					void single_list::insert_pos()
					{
						int value,pos,counter=0,loc=1;
						struct node *temp,*s,*ptr;
						s=start;
						while(s!=NULL)
						{
							s=s->next;
							counter++;
						}
						if(counter==0)
						{
						}
						else
						{
							cout<<"enter the position from"<<loc<<"to"<<counter+1<<":";
							cin>>pos;
							s=start;
							if(pos==1)
							{
								cout<<"enter the value to be inserted:";
								cin>>value;
								temp=create_node(value);
								start=temp;
								start->next-s;
								cout<<temp->info<<"is inserted at first"<<endl;
							}
							else if(pos>1 && pos<=counter)
							{
								cout<<"enter the value to be inserted:";
								cin>>value;
								temp=create_node(value);
								for(int i=1;i<pos;i++)
								{
									ptr=s;
									s=s->next;
								}
								ptr->next=temp;
								temp->next=s;
								cout<<temp->info<<"is inserted at position"<<pos<<endl;
							}
							else if(pos==counter+1)
							{
								cout<<"enter the value to be inserted:";
								cin>>value;
								temp=create_node(value);
								while(s->next!=NULL)
								{
									s=s->next;
								}
								temp->next=NULL;
								s->next=temp;
								cout<<temp->info<<"is inserted at last"<<endl;
								
							}
							else
							{
								cout<<"position out of range...!!!"<<endl;
							}
						
							}
						}
						void single_list::delete_begin()
						{
							if(start==NULL)
							{
							}
							else
							{
							struct node *s,*ptr;
							s=start;
							start=s->next;
							cout<<s->info<<"deleted from first"<<endl;
							free(s);	
							}
						}
						void single_list::delete_last()
						{
							int i,counter=0;
							struct node *s,*ptr;
							if(start==NULL)
							{
							}
							else
							{
								s=start;
								while(s!=NULL)
								{
									s=s->next;
									counter++;
									
								}
								s=start;
								if(counter==1)
								{
									start=s->next;
									cout<<s->info<<"deleted from last"<<endl;
									free(s);
									
								}
								else
								{
									for(i=1;i<counter;i++)
									{
										ptr=s;
										s=s->next;
									}
									ptr->next=s->next;
									cout<<s->info<<"deleted from last"<<endl;
									free(s);
								}
							}
						}
						void single_list::delete_pos()
						{
							int pos,i,counter=0,loc=1;
							struct node *s,*ptr;
							s=start;
							while(s!=NULL)
							{
								s=s->next;
								counter++;
							}
							if(counter==0)
							{
							}
							else
							{
								if(counter==1)
							{
							 
   
 cout<<"Enter the postion [ SAY "<<loc<<" ] : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1) 
 { 
 start = s->next; 
 cout<<s->info<<" deleted from first"<<endl; 
 free(s); 
 } 
else
cout<<"position out of range...!!!"<<endl;
}
else 
 { 
 cout<<"Enter the postion from "<<loc<<" to "<<counter<<" : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1) 
 { 
 start = s->next; 
  cout<<s->info<<" deleted from first"<<endl; 
 free(s); 
 } 
 else if (pos > 1 && pos <= counter) 
 { 
 for (i = 1;i < pos;i++) 
 { 
 ptr = s; 
 s = s->next; 
 } 
 ptr->next = s->next; 
 if(pos == counter) 
 {cout<<s->info<<" deleted from last"<<endl; 
 free(s);} 
 else 
 {cout<<s->info<<" deleted from postion "<<pos<<endl; 
 free(s);} 
 } 
 else 
 cout<<"Position out of range...!!!"<<endl; 
 } 
 } 
} 
void single_list::update_begin() 
{ 
 int value, pos=1, i,counter = 0; 
 struct node *s, *ptr; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 if (counter == 0){} 
 else if (pos == 1) 
 { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 start->info = value; 
 cout<<"Node updated at first position : "<<pos<<" = "<<start->info<<endl; 
 } 
} 
void single_list::update_last() 
{ 
 int value, pos, i,counter = 0; 
 struct node *s, *ptr; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 s=start; 
 if (counter == 0){} 
 else 
 {
 cout<<"Enter the new node : "; 
 cin>>value; 
 for (i = 1; i < counter ; i++) 
 { 
 s = s->next; 
 } 
 s->info = value; 
 cout<<"Node updated at last position : "<<counter<<" = "<<s->info<<endl; 
 } 
} 
void single_list::update_pos() 
{ 
 int value, pos, i,counter = 0, loc = 1; 
 struct node *s, *ptr; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 if (counter == 0){} 
 else 
 { 
 if (counter == 1) 
 { 
 cout<<"Enter the postion [ SAY "<<loc<<" ] : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1)
  { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 start->info = value; 
 cout<<"Node updated at position : "<<pos<<" = "<<start->info<<endl; 
 } 
 else 
 cout<<"Position out of range...!!!"<<endl; 
 } 
 else 
 { 
 cout<<"Enter the postion from "<<loc<<" to "<<counter<<" : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1) 
 { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 start->info = value; 
 cout<<"Node updated at position : "<<pos<<" = "<<start->info<<endl; 
 } 
 else if (pos > 1 && pos <= counter) 
 { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 for (i = 1; i < pos ; i++) 
 { 
 s = s->next; 
 } 
 s->info = value; 
 cout<<"Node updated at position : "<<pos<<" = "<<s->info<<endl; 
 } 
 else 
 cout<<"Position out of range...!!!"<<endl; 
 } 
 } 
} 
void single_list::sort() 
{ 
 struct node *ptr, *s; 
 int value; 
 if (start == NULL){} 
 else 
 { 
 ptr = start; 
 while (ptr != NULL) 
 { 
 for (s = ptr->next;s !=NULL;s = s->next) 
 { 
 if (ptr->info > s->info) 
 { 
 value = ptr->info; 
 ptr->info = s->info; 
 s->info = value; 
 } 
 }
 ptr = ptr->next; 
 } 
 } 
} 
void single_list::reverse() 
{ 
 struct node *ptr, *s; 
 int value; 
 if (start == NULL){} 
 else 
 { 
 ptr = start; 
 while (ptr != NULL) 
 { 
 for (s = ptr->next;s !=NULL;s = s->next) 
 { 
 if (ptr->info < s->info) 
 { 
 value = ptr->info; 
 ptr->info = s->info; 
 s->info = value; 
 } 
 } 
 ptr = ptr->next; 
 } 
 } 
} 
void single_list::search() 
{ 
 int value, loc = 0, pos = 0, counter = 0; 
 struct node *s; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 if (start == NULL){} 
 else 
 { 
 cout<<"Enter the value to be searched : "; 
 cin>>value; 
 struct node *s; 
 s = start; 
 while (s != NULL) 
 { 
 pos++; 
 if (s->info == value) 
 { 
 loc++; 
 if(loc == 1) 
 cout<<"Element "<<value<<" is found at position "<<pos; 
 else if(loc <= counter) 
 cout<<" , "<<pos; 
 } 
 s = s->next; 
 } 
 cout<<endl; 
 if (loc == 0) 
 cout<<"Element "<<value<<" not found in the list"<<endl; 
 } 
} 
void single_list::display() 
{ 
 struct node *temp; 
 if (start == NULL) 
 cout<<"Linked list is empty...!!!"<<endl; 
 else 
 { 
 cout<<"Linked list contains : "; 
 temp = start; 
 while (temp != NULL) 
 { 
 cout<<temp->info<<" "; 
 
 temp = temp->next; 
 } 
 cout<<endl; 
 } 
}
  <br>
  #include<iostream>
#include<cstdlib>
using namespace std;
struct node
{
	int info;
	struct node *next;
}*start;
class single_list
{
	public:
		node*create_node(int);
		void insert_begin();
		void insert_last();
		void insert_pos();
		void delete_pos();
		void delete_begin();
		void delete_last();
		void update_begin();
		void update_last();
		void update_pos();
		void sort();
		void reverse();
		void search();
		void display();
		single_list()
		{
			start=NULL;
		}
};
int main()
{
	int choice;
	single_list s1,s2;
	start=NULL;
	do
	{
		cout<<"----------"<<endl;
		cout<<"operations on singly linked list"<<endl;
		cout<<"--------------------------"<<endl;
		cout<<"1.insert at first"<<endl;
		cout<<"2.insert at last"<<endl;
		cout<<"3.insert at position"<<endl;
		cout<<"4.delete at first"<<endl;
		cout<<"5.delete at last"<<endl;
		cout<<"6.delete at position"<<endl;
		cout<<"7.update at first"<<endl;
		cout<<"8.update at last"<<endl;
		cout<<"9.update at position"<<endl;
		cout<<"10.ascending order"<<endl;
		cout<<"11.descending order"<<endl;
		cout<<"12.search"<<endl;
		cout<<"13.display"<<endl;
		cout<<"14.exit"<<endl;
		cout<<"enter your choice:";
		cin>>choice;
		switch(choice)
		{
			case 1:s1.insert_begin();
			s1.display();
			break;
			case 2:s1.insert_last();
			s1.display();
			break;
			case 3:s1.insert_pos();
			s1.display();
			break;
			case 4:s2.delete_begin();
			s1.display();
			break;
			case 5:s2.delete_last();
			s1.display();
			break;
			case 6:s1.delete_pos();
			s1.display();
			break;
			case 7:s1.update_begin();
			s1.display();
			break;
			case 8:s1.update_last();
			s1.display();
			break;
			case 9:s1.update_pos();
			s1.display();
			break;
			case 10:s1.sort();
			s1.display();
			break;
			case 11:s1.reverse();
			s1.display();
			break;
			case 12:s1.search();
			s1.display();
			break;
			case 13:s1.display();
			break;
			case 14:exit(0);
			break;
			default:cout<<"wrong choice...???"<<endl;
			break;
		}
	}
	while(choice!=14);
}
node *single_list::create_node(int value)
{
	struct node *temp,*s;
	temp=new(struct node);
	if(temp==NULL)
	{
		cout<<"memory not allocated"<<endl;
		return 0;
	}
	else
	{
		temp->info=value;
		temp->next=NULL;
		return temp;
	}
}
void single_list::insert_begin()
{
	int value;
	cout<<"enter the value to be inserted:";
	cin>>value;
	struct node *temp,*s;
	temp=create_node(value);
	if(start==NULL)
	{
		start=temp;
		start->next=NULL;
		cout<<temp->info<<"is inserted at first in the empty list"<<endl;
	
	}
	else
	{
		s=start;
		start=temp;
		start->next=s;
		cout<<temp->info<<"is inserted at first"<<endl;
		
	}
			}
			void single_list::insert_last()	
			{
				int value;
				cout<<"enter the value to be inserted:";
				cin>>value;
				struct node *temp,*s;
				temp=create_node(value);
				if(start==NULL)
				{
					start=temp;
					start->next=NULL;
					cout<<temp->info<<"is inserted at last in the empty list"<<endl;
					
				}
				else
				{
					s=start;
					while(s->next!=NULL)
					{
					
					s=s->next;
					}
					temp->next=NULL;
					s->next=temp;
					cout<<temp->info<<"is inserted at last"<<endl;
				}
					}
					void single_list::insert_pos()
					{
						int value,pos,counter=0,loc=1;
						struct node *temp,*s,*ptr;
						s=start;
						while(s!=NULL)
						{
							s=s->next;
							counter++;
						}
						if(counter==0)
						{
						}
						else
						{
							cout<<"enter the position from"<<loc<<"to"<<counter+1<<":";
							cin>>pos;
							s=start;
							if(pos==1)
							{
								cout<<"enter the value to be inserted:";
								cin>>value;
								temp=create_node(value);
								start=temp;
								start->next-s;
								cout<<temp->info<<"is inserted at first"<<endl;
							}
							else if(pos>1 && pos<=counter)
							{
								cout<<"enter the value to be inserted:";
								cin>>value;
								temp=create_node(value);
								for(int i=1;i<pos;i++)
								{
									ptr=s;
									s=s->next;
								}
								ptr->next=temp;
								temp->next=s;
								cout<<temp->info<<"is inserted at position"<<pos<<endl;
							}
							else if(pos==counter+1)
							{
								cout<<"enter the value to be inserted:";
								cin>>value;
								temp=create_node(value);
								while(s->next!=NULL)
								{
									s=s->next;
								}
								temp->next=NULL;
								s->next=temp;
								cout<<temp->info<<"is inserted at last"<<endl;
								
							}
							else
							{
								cout<<"position out of range...!!!"<<endl;
							}
						
							}
						}
						void single_list::delete_begin()
						{
							if(start==NULL)
							{
							}
							else
							{
							struct node *s,*ptr;
							s=start;
							start=s->next;
							cout<<s->info<<"deleted from first"<<endl;
							free(s);	
							}
						}
						void single_list::delete_last()
						{
							int i,counter=0;
							struct node *s,*ptr;
							if(start==NULL)
							{
							}
							else
							{
								s=start;
								while(s!=NULL)
								{
									s=s->next;
									counter++;
									
								}
								s=start;
								if(counter==1)
								{
									start=s->next;
									cout<<s->info<<"deleted from last"<<endl;
									free(s);
									
								}
								else
								{
									for(i=1;i<counter;i++)
									{
										ptr=s;
										s=s->next;
									}
									ptr->next=s->next;
									cout<<s->info<<"deleted from last"<<endl;
									free(s);
								}
							}
						}
						void single_list::delete_pos()
						{
							int pos,i,counter=0,loc=1;
							struct node *s,*ptr;
							s=start;
							while(s!=NULL)
							{
								s=s->next;
								counter++;
							}
							if(counter==0)
							{
							}
							else
							{
								if(counter==1)
							{
							 
   
 cout<<"Enter the postion [ SAY "<<loc<<" ] : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1) 
 { 
 start = s->next; 
 cout<<s->info<<" deleted from first"<<endl; 
 free(s); 
 } 
else
cout<<"position out of range...!!!"<<endl;
}
else 
 { 
 cout<<"Enter the postion from "<<loc<<" to "<<counter<<" : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1) 
 { 
 start = s->next; 
  cout<<s->info<<" deleted from first"<<endl; 
 free(s); 
 } 
 else if (pos > 1 && pos <= counter) 
 { 
 for (i = 1;i < pos;i++) 
 { 
 ptr = s; 
 s = s->next; 
 } 
 ptr->next = s->next; 
 if(pos == counter) 
 {cout<<s->info<<" deleted from last"<<endl; 
 free(s);} 
 else 
 {cout<<s->info<<" deleted from postion "<<pos<<endl; 
 free(s);} 
 } 
 else 
 cout<<"Position out of range...!!!"<<endl; 
 } 
 } 
} 
void single_list::update_begin() 
{ 
 int value, pos=1, i,counter = 0; 
 struct node *s, *ptr; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 if (counter == 0){} 
 else if (pos == 1) 
 { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 start->info = value; 
 cout<<"Node updated at first position : "<<pos<<" = "<<start->info<<endl; 
 } 
} 
void single_list::update_last() 
{ 
 int value, pos, i,counter = 0; 
 struct node *s, *ptr; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 s=start; 
 if (counter == 0){} 
 else 
 {
 cout<<"Enter the new node : "; 
 cin>>value; 
 for (i = 1; i < counter ; i++) 
 { 
 s = s->next; 
 } 
 s->info = value; 
 cout<<"Node updated at last position : "<<counter<<" = "<<s->info<<endl; 
 } 
} 
void single_list::update_pos() 
{ 
 int value, pos, i,counter = 0, loc = 1; 
 struct node *s, *ptr; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 if (counter == 0){} 
 else 
 { 
 if (counter == 1) 
 { 
 cout<<"Enter the postion [ SAY "<<loc<<" ] : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1)
  { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 start->info = value; 
 cout<<"Node updated at position : "<<pos<<" = "<<start->info<<endl; 
 } 
 else 
 cout<<"Position out of range...!!!"<<endl; 
 } 
 else 
 { 
 cout<<"Enter the postion from "<<loc<<" to "<<counter<<" : "; 
 cin>>pos; 
 s = start; 
 if (pos == 1) 
 { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 start->info = value; 
 cout<<"Node updated at position : "<<pos<<" = "<<start->info<<endl; 
 } 
 else if (pos > 1 && pos <= counter) 
 { 
 cout<<"Enter the new node : "; 
 cin>>value; 
 for (i = 1; i < pos ; i++) 
 { 
 s = s->next; 
 } 
 s->info = value; 
 cout<<"Node updated at position : "<<pos<<" = "<<s->info<<endl; 
 } 
 else 
 cout<<"Position out of range...!!!"<<endl; 
 } 
 } 
} 
void single_list::sort() 
{ 
 struct node *ptr, *s; 
 int value; 
 if (start == NULL){} 
 else 
 { 
 ptr = start; 
 while (ptr != NULL) 
 { 
 for (s = ptr->next;s !=NULL;s = s->next) 
 { 
 if (ptr->info > s->info) 
 { 
 value = ptr->info; 
 ptr->info = s->info; 
 s->info = value; 
 } 
 }
 ptr = ptr->next; 
 } 
 } 
} 
void single_list::reverse() 
{ 
 struct node *ptr, *s; 
 int value; 
 if (start == NULL){} 
 else 
 { 
 ptr = start; 
 while (ptr != NULL) 
 { 
 for (s = ptr->next;s !=NULL;s = s->next) 
 { 
 if (ptr->info < s->info) 
 { 
 value = ptr->info; 
 ptr->info = s->info; 
 s->info = value; 
 } 
 } 
 ptr = ptr->next; 
 } 
 } 
} 
void single_list::search() 
{ 
 int value, loc = 0, pos = 0, counter = 0; 
 struct node *s; 
 s = start; 
 while (s != NULL) 
 { 
 s = s->next; 
 counter++; 
 } 
 if (start == NULL){} 
 else 
 { 
 cout<<"Enter the value to be searched : "; 
 cin>>value; 
 struct node *s; 
 s = start; 
 while (s != NULL) 
 { 
 pos++; 
 if (s->info == value) 
 { 
 loc++; 
 if(loc == 1) 
 cout<<"Element "<<value<<" is found at position "<<pos; 
 else if(loc <= counter) 
 cout<<" , "<<pos; 
 } 
 s = s->next; 
 } 
 cout<<endl; 
 if (loc == 0) 
 cout<<"Element "<<value<<" not found in the list"<<endl; 
 } 
} 
void single_list::display() 
{ 
 struct node *temp; 
 if (start == NULL) 
 cout<<"Linked list is empty...!!!"<<endl; 
 else 
 { 
 cout<<"Linked list contains : "; 
 temp = start; 
 while (temp != NULL) 
 { 
 cout<<temp->info<<" "; 
 
 temp = temp->next; 
 } 
 cout<<endl; 
 } 
}

<br>
  **output**
  
![image](https://user-images.githubusercontent.com/98379636/156984679-9fa8ac23-7235-4690-9f50-27cf3accf4cf.png)
  ![image](https://user-images.githubusercontent.com/98379636/156985197-2aa81db8-d8aa-4a3d-8106-1778dba735b2.png
	![image](https://user-images.githubusercontent.com/98379636/156986219-58a8216f-db3d-4829-b4fa-68d11e65d659.png)
	![image](https://user-images.githubusercontent.com/98379636/156986436-49535788-3e2e-42e8-b2d7-d64a3d3a80fb.png)
	![image](https://user-images.githubusercontent.com/98379636/156986849-1b2f02e4-7036-4340-8299-a99a3e2a54f8.png)
	![image](https://user-images.githubusercontent.com/98379636/156987037-61df715e-6514-434b-98b1-4ad14572aa83.png)
	![image](https://user-images.githubusercontent.com/98379636/156987232-8dff16af-ebbf-4eb3-ba6c-dc25d25e9d0b.png)
	![image](https://user-images.githubusercontent.com/98379636/156987360-4155ee1c-abe4-4cd4-ae06-694d90451bdc.png)
	![image](https://user-images.githubusercontent.com/98379636/156987437-57a2d107-c55a-4e5d-93f8-fc190e7262d3.png)
	![image](https://user-images.githubusercontent.com/98379636/156987523-9b64f318-06cd-44ed-9e39-3fe6db8341fa.png)
	![image](https://user-images.githubusercontent.com/98379636/156987663-7042c120-5761-4fda-a449-e43a2c206963.png)
	![image](https://user-images.githubusercontent.com/98379636/156987785-f005ccf0-6843-44fb-9cda-31c7dc6d8b35.png)
	![image](https://user-images.githubusercontent.com/98379636/156987906-20201449-ef81-4193-8036-2f341d4e43fc.png)
	![image](https://user-images.githubusercontent.com/98379636/156987984-3d36eb26-d744-47f5-90d6-a9a88c956c3d.png)
	
	
	**hashtable**
	
#include<iostream>
#include<limits.h>
using namespace std;
void Insert(int ary[],int hFn, int Size)
{
int element,pos,n=0;
cout<<"Enter key element to insert\n";
cin>>element;
pos = element%hFn;
while(ary[pos]!= INT_MIN)
{
if(ary[pos]== INT_MAX)
break;
pos = (pos+1)%hFn;
n++;
if(n==Size)
break;
}
if(n==Size)
cout<<"Hash table was full of elements\nNo Place to insert this element\n\n";
else
ary[pos] = element;
}
void display(int ary[],int Size)
{
int i;
cout<<"Index\tValue\n";
for(i=0;i<Size;i++)
cout<<i<<"\t"<<ary[i]<<"\n";
}
int main()
{
int Size,hFn,i,choice;
cout<<"Enter size of hash table\n";
cin>>Size;
hFn=Size;
int ary[Size];
for(i=0;i<Size;i++)
ary[i]=INT_MIN;
do
{
cout<<"Enter your choice\n";
cout<<" 1-> Insert\n 2-> Display\n 0-> Exit\n";
cin>>choice;
switch(choice)
{
case 1: Insert(ary,hFn,Size);
break;
case 2: display(ary,Size);
break;
default: cout<<"Enter correct choice\n";
break;
}
}
while(choice);
return 0;
}
<br>
	**output**
	![image](https://user-images.githubusercontent.com/98379636/157167830-f2308df6-5d52-44cb-baac-3e98e923fd20.png)
	
	
**minheap**
	
#include<iostream>	
#include <conio.h>
using namespace std;
void min_heap(int *a, int m, int n){
   int j, t;
   t= a[m];
   j = 2 * m;
   while (j <= n) {
      if (j < n && a[j+1] < a[j])
         j = j + 1;
      if (t < a[j])
         break;
      else if (t >= a[j]) {
         a[j/2] = a[j];
         j = 2 * j;
      }
   }
   a[j/2] = t;
   return;
}
void build_minheap(int *a, int n) {
   int k;
   for(k = n/2; k >= 1; k--) {
      min_heap(a,k,n);
   }
}
int main() {
   int n, i;
   cout<<"enter no of elements of array\n";
   cin>>n;
   int a[30];
   for (i = 1; i <= n; i++) {
      cout<<"enter element"<<" "<<(i)<<endl;
      cin>>a[i];
   }
   build_minheap(a, n);
   cout<<"Min Heap\n";
   for (i = 1; i <= n; i++) {
      cout<<a[i]<<endl;
   }
   getch();
}
<br>
**output**
	![image](https://user-images.githubusercontent.com/98379636/157168974-a0de1ace-8ca4-4983-ab29-85ce1cc89e67.png)
	
	**maxheap**
	
using namespace std;
void max_heap(int *a, int m, int n) {
   int j, t;
   t = a[m];
   j = 2 * m;
   while (j <= n) {
      if (j < n && a[j+1] > a[j])
         j = j + 1;
      if (t > a[j])
         break;
      else if (t <= a[j]) {
         a[j / 2] = a[j];
         j = 2 * j;
      }
   }
   a[j/2] = t;
   return;
}
void build_maxheap(int *a,int n) {
   int k;
   for(k = n/2; k >= 1; k--) {
      max_heap(a,k,n);
   }
}
int main() {
   int n, i;
   cout<<"enter no of elements of array\n";
   cin>>n;
   int a[30];
   for (i = 1; i <= n; i++) {
      cout<<"enter elements"<<" "<<(i)<<endl;
      cin>>a[i];
   }
   build_maxheap(a,n);
   cout<<"Max Heap\n";
   for (i = 1; i <= n; i++) {
      cout<<a[i]<<endl;
   }
}
		       <br>
	**output**
	![image](https://user-images.githubusercontent.com/98379636/157170243-09cf454a-ff87-4e94-b015-5bde6beef8e8.png)
	
	**doublylinkedlist**
	#include<iostream>
using namespace std;
struct Node {
   int data;
   struct Node *prev;
   struct Node *next;
};
struct Node* head = NULL;
void insert(int newdata) {
   struct Node* newnode = (struct Node*) malloc(sizeof(struct Node));
   newnode->data = newdata;
   newnode->prev = NULL;
   newnode->next = head;
   if(head != NULL)
   head->prev = newnode ;
   head = newnode;
}
void display() {
   struct Node* ptr;
   ptr = head;
   while(ptr != NULL) {
      cout<< ptr->data <<" ";
      ptr = ptr->next;
   }
}
int main() {
   insert(3);
   insert(1);
   insert(7);
   insert(2);
   insert(9);
   cout<<"The doubly linked list is: ";
   display();
   return 0;
}
<br>
	**output**
	![image](https://user-images.githubusercontent.com/98379636/157182852-d6a68d6b-9515-496e-ba04-008980ced5f9.png)
	
	**splitting**
	
using namespace std;
void MaxHeapify (int a[], int i, int n)
{
int j, temp;
temp = a[i];
j =2i;
while (j <= n)
{
if (j < n && a[j+1] > a[j])
j = j+1;
if (temp > a[j])
break;
else if (temp <= a[j])
{
a[j/2] = a[j];
i = 2j;
}
}
a[j/2] = temp;
return;
}
void HeapSort(int a[], int n)
{
int i, temp;
for (i = n; i >= 2; i--)
{
temp = a[i];
a[i] = a[1];
a[1] = temp;
MaxHeapify(a, 1, i - 1);
}
}
void Build_MaxHeap(int a[], int n)
{
int i;
for(i = n/2; i >= 1; i--)
MaxHeapify(a, i, n);
}
int main()
{
int n, i,arr[100];
cout<<"\nEnter the number of data element to be sorted: ";
cin>>n;
n++;
for(i=1;i<n;i++)
{
cout<<"Enter element"<<i<<":";
cin>>arr[i];
}
Build_MaxHeap(arr, n-1);
HeapSort(arr, n-1);
cout<<"\nSorted Data ";
for (i = 1; i < n; i++)
cout<<" "<<arr[i];
return 0;
}

<br>
	**output**
	
	![image](https://user-images.githubusercontent.com/98379636/157184165-20632450-4a53-42c8-8cd8-a753da210abe.png)
	
	**minheap**
	#include<iostream>
#include <conio.h>
using namespace std;
void min_heap(int *a, int m, int n){
   int j, t;
   t= a[m];
   j = 2 * m;
   while (j <= n) {
      if (j < n && a[j+1] < a[j])
         j = j + 1;
      if (t < a[j])
         break;
      else if (t >= a[j]) {
         a[j/2] = a[j];
         j = 2 * j;
      }
   }
   a[j/2] = t;
   return;
}
void build_minheap(int *a, int n) {
   int k;
   for(k = n/2; k >= 1; k--) {
      min_heap(a,k,n);
   }
}
int main() {
   int n, i;
   cout<<"enter no of elements of array\n";
   cin>>n;
   int a[30];
   for (i = 1; i <= n; i++) {
      cout<<"enter element"<<" "<<(i)<<endl;
      cin>>a[i];
   }
   build_minheap(a, n);
   cout<<"Min Heap\n";
   for (i = 1; i <= n; i++) {
      cout<<a[i]<<endl;
   }
   getch();
}

<br>
	**output**
	![image](https://user-images.githubusercontent.com/98379636/159210874-d67da3be-038e-44c5-939f-8de92ed6e265.png)

	


	

	

	


	
	
		       

	
	

	



















 
 
 



			
									
			
		
		
		
	
