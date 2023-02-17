#include <iostream>
using namespace std;

class node{
    public:
    int data;
    node* next;
    node(int value){
        data=value;
        next=NULL;
    }
};
//👉 Insertion at head
void insertAtHead(node* &head,int data){
    node* temp=new node(data);
    temp->next=head;
    head->next=NULL;
    head=temp;
    
}
//👉insertion at tail
void insertAtTail(node* &head,int data){
    node* temp=new node(data);
    head->next=temp;
    temp->next=NULL;
    head=temp;
}
//👉inserting at middle
 void insertAtmiddle(node* &tail,node* &head,int position,int data){
     node* temp=head;
     if(position==1){
         insertAtHead(head,data);
         return;
     }
     int cnt=0;
     while(cnt<position){
         temp=temp->next;
         cnt++;
     }
     if(temp->next==NULL){
         insertAtTail(tail,data);
         return;
     }
     
     node* insert=new node(data);
     insert->next=temp->next;
     temp->next=insert;
     
 }
 void deleteNode(node* &head,int value){
  if(head->data==value){
      head=head->next;
  }
  else{
     node* prev=NULL;
     node* curr=head;
     while(curr->data!=value){
         prev=curr;
         curr=curr->next;
     }
     prev->next=curr->next;
 }}
//👉print function
void print(node* &head){
    node* temp=head;
    while(temp!=NULL){
        cout<<temp->data<<" ";
        temp=temp->next;
    }
}
int main() {
    node* node1=new node(1);
    // cout<<node1->data<<" "<<node1->next;
     node* head=node1;
     node* tail=node1;
     
    //👉calling insert at head
        // insertAtHead(head,11);
        // insertAtHead(head,12);
        
    //👉calling insert at tail  
        insertAtTail(tail,2);
        insertAtTail(tail,3);
        insertAtTail(tail,4);
        insertAtmiddle(tail,head,2,33);
        insertAtmiddle(tail,head,4,22);
     print(head);
     cout<<endl;
     deleteNode(head,2);
     deleteNode(head,22);
     deleteNode(head,1);
     print(head);
    return 0;
}
