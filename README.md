# swap-kth-node
import java.util.*;
import java.lang.*;
import java.io.*;

public class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
		Scanner sc=new Scanner(System.in);
                int n=sc.nextInt();
                int k=sc.nextInt();
                check p=new check();
                for(int i=0;i<n;i++){
                        p.add(sc.nextInt());
                }
                p.swap(k);
                p.print();
	}
}
class check{
        Node head;
        Node tail;
        void add(int data){
                Node newnode=new Node(data);
                if(head==null){
                        head=newnode;
                        tail=newnode;
                }
               tail.next=newnode;
                tail=newnode;
        }
         void print(){
           Node temp=head;
                 while(temp!=null){
                         System.out.print(temp.data+" ");
                         temp=temp.next;
                 }
         }
        int count(){
                int size=0;
                Node temp=head;
                while(temp!=null){
                        size++;
                        temp=temp.next;
                }
                return size;
        }
     
        void swap(int k){
                int n=count();
                if(n<k)
                        return;
                
                if(2*k-1==n)
                        return;
                
                Node x=head;
                Node prev=null;
                for(int i=1;i<k;i++){
                        prev=x;
                        x=x.next;
                        
                }
                Node y=head;
                Node pre=null;
                for(int i=1;i<n-k+1;i++){
                        pre=y;
                        y=y.next;
                }
                if(prev!=null)
                        prev.next=y;
                
                if(pre!=null)
                        pre.next=x;
                
                Node temp=x.next;
                x.next=y.next;
                y.next=temp;
        
        if(k==1)
        head=y;
        
        
if(k==n)
        head=x;
}

}
class Node{
        int data;
        Node next;
      Node(int data){
              this.data=data;
              this.next=null;
      }
}
