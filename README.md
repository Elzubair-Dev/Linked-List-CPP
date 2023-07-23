# Linked-List-CPP
Linked List is one of the basic concepts of data structures
     
## Code:
    
```
using namespace std;
#include<iostream>
class Linked_List
{
private:
	struct node
	{
		int item;
		node* next;
	};
	node* head;
	node* rear;
	node* temp;
	int count;
public:
	Linked_List()
	{
		head = rear = temp = NULL;
		count = 0;
	}
	bool isEmpty()
	{
		return count == 0;
	}
	void add_first(int Element)
	{
		node* newnode = new node;
		newnode->item = Element;
		if (isEmpty())
		{
			head = rear = newnode;
			newnode->next = NULL;
			count++;
		}
		else
		{
			temp = head;
			head = newnode;
			newnode->next = temp;
			count++;
		}
	}
	void add_last(int Element)
	{
		node* newnode = new node;
		newnode->item = Element;
		if (isEmpty())
		{
			head = rear = newnode;
			newnode->next = NULL;
			count++;
		}
		else
		{
			temp = rear;
			rear = newnode;
			temp->next = newnode;
			newnode->next = NULL;
			count++;
		}
	}
	void add_mid(int pos , int Element)
	{
		if (pos < 0 || pos > count + 1) cout << "Out of range...\n";
		else
		{
			if (isEmpty())
			{
				node* newnode = new node;
				newnode->item = Element;
				head = rear = newnode;
				newnode->next = NULL;
				count++;
			}
			else if (count == 1 && pos == 0)
			{
				add_first(Element);
			}
			else if (count == 1 && pos == 1)
			{
				add_last(Element);
			}
			else
			{
				node* newnode = new node;
				newnode->item = Element;
				temp = head;
				for (int i = 0; i < pos - 1; i++)
				{
					temp = temp->next;
				}
				newnode->next = temp->next;
				temp->next = newnode;
				count++;
			}
		}
		
	}
	void remove_last()
	{
		node* nxt = new node;
		if (isEmpty()) cout << "Oops! Can't delete an empty list...\n";
		else if (count == 1)
		{
			nxt = rear;
			head = rear = NULL;
			delete nxt;
			count--;
		}
		else
		{
			temp = head;
			while (temp->next != rear)
			{
				temp = temp->next;
			}
			nxt = rear;
			temp->next = NULL;
			rear = temp;
			delete nxt;
			count--;
		}
	}
	void remove_first()
	{
		if (isEmpty()) cout << "Oops! Can't delete an empty list...\n";
		else if (count == 1)
		{
			temp = head;
			head = rear = NULL;
			delete temp;
			count--;
		}
		else
		{
			temp = head;
			head = head->next;
			delete temp;
			count--;
		}
	}
	void remove_mid(int pos)
	{
		if (pos < 0 || pos > count - 1)cout << "Out of range\n";
		else
		{
			if (isEmpty()) cout << "Oops! Can't delete an empty list...\n";
			else if (count == 1)
			{
				temp = head;
				head = rear = NULL;
				delete temp;
				count--;
			}
			else
			{
				if (pos == 0)
				{
					remove_first();
				}
				else if (pos == count - 1)
				{
					remove_last();
				}
				else
				{
					node* prev = new node;
					temp = head;
					prev->next = temp;
					for (int i = 0; i < pos; i++)
					{
						temp = temp->next;
						prev = prev->next;
					}
					prev->next = temp->next;
					delete temp;
					count--;
				}
			}
		}
	}
	void remove_item(int item)
	{
		int pos = -1;
		temp = head;
		if (isEmpty()) cout << "Oops! Can't delete an empty list...\n";
		else
		{
			for (int i = 0; i <= count - 1; i++)
			{
				pos++;
				if (temp->item == item)
				{
					if (pos == 0)
					{
						remove_first();
						break;
					}
					else if (pos == count - 1)
					{
						remove_last();
						break;
					}
					else
					{
						remove_mid(pos);
						break;
					}
				}
				else
				{
					temp = temp->next;
				}
			}
		}
	}
	int search(int Element)
	{
		if (isEmpty()) cout << "Oops! it's an empty list...\n";
		else
		{
			int pos = -1;
			temp = head;
			for (int i = 0; i < count; i++)
			{
				pos++;
				if (temp->item == Element)
				{
					return pos;
					break;
				}
				else
				{
					temp = temp->next;
					if (pos == count - 1)
					{
						pos = -1;
						return pos;
					}
				}
			}
			
		}
	}
	void reverse()
	{
		if (isEmpty()||count == 1) cout << "Oops! Can't reverse an empty or one item list...\n";
		else 
		{
			node* nxt = new node;
			node* prv = new node;
			temp = head;
			nxt = temp->next;
			prv = NULL;
			while (temp != NULL)
			{
				nxt = temp->next;
				temp->next = prv;
				prv = temp;
				temp = nxt;
			}
			head = prv;
		}
	}
	void Display()
	{
		temp = head;
		cout << "[ ";
		while (temp != NULL)
		{
			cout << temp->item <<" ";
			temp = temp->next;
		}
		cout << "]\n";
	}
};
int main()
{
	Linked_List l;
	int n = 10;
	l.add_first(n);
	l.add_first(5);
	l.add_last(20);
	l.add_mid(2, 15);
	l.remove_item(20);
	l.Display();
}
```

## Buy me a Coffee:
if you want to support me
(https://www.buymeacoffee.com/zu698air)

#### Don't forgit to give me a Star

## Done
