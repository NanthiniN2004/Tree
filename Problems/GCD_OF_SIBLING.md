## WRITE A JAVA PROGRAM FIND MAXIMUM GCD OF THE SIBLINGS
````java[]

import java.util.*;

class Node{
	int data;
	Node left,right;
	Node(int data){
		this.data=data;
		this.left=null;
		this.right=null;
		}
}
class Binarytree{
	Node root;
public Node insert(Node root,int data)
	{
		Node newnode=new Node(data);
		if(root==null) {
			return newnode;
		}
		Node tptr=root;
		Node temp=null;
		while(tptr !=null) {
			temp=tptr;
			if(tptr.data>data) {
				tptr=tptr.left;
			}
			else {
				tptr=tptr.right;
			}
		}
		if(temp.data>data) {
			temp.left=newnode;
			
		}
		else {
			temp.right=newnode;
		}
		return root;
	}
	public  void insertrev(int data)
	{
		root=insert(root,data);
	}
	
	public void preorder(Node root) {
		if(root !=null) {
			System.out.print(root.data+" ");
			preorder(root.left);
			preorder(root.right);
			
		}
	}
	
 public int gcd(int a,int b){
     if(b==0){
         return a;
     }
     return gcd(b,a%b);
 }
 
 public int findgcd(Node root){
     if(root==null)
     {
         return 0;
     }
     Queue<Node> q=new LinkedList<>();
     q.add(root);
     int maxgcd=0;
     while(!q.isEmpty()){
         Node temp=q.poll();
         if(temp.left != null)
         {
             q.add(temp.left);
         }
         if(temp.right != null)
         {
             q.add(temp.right);
         }
         
         if(temp.left !=null && temp.right !=null)
         {
             int gcd=gcd(temp.left.data,temp.right.data);
              System.out.println("gcd of each level of sibling: "+ temp.left.data + " and "+ temp.right.data +" : " +gcd);
             maxgcd=Math.max(gcd,maxgcd);
         }
     }
     return maxgcd;
     
 }
}
public class Main {

	public static void main(String[] args) {
	  Scanner s=new Scanner(System.in);
	  Binarytree obj=new Binarytree();
	  int n=s.nextInt();
	  for(int i=0;i<n;i++) {
		  int val=s.nextInt();
		 
		  obj.insertrev(val);
	  }
	  System.out.println("pre order Traversal "  );
	obj.preorder(obj.root) ;
	System.out.println("Maximum gcd value of the siblings " + obj.findgcd(obj.root));
	  

	}

}


OUTPUT:
7
20
10
30
5
15
25
35
pre order Traversal 
20 10 5 15 30 25 35 gcd of each level of sibling: 10 and 30 : 10
gcd of each level of sibling: 5 and 15 : 5
gcd of each level of sibling: 25 and 35 : 5
Maximum gcd value of the siblings 10

`````

