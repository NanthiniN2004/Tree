## WRITE A JAVA PROGRAM CHECK WHETHER TREE IS BINARY SEARCH TREE OR NOT

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
	public  void insert( int data) {
		Node newnode=new Node(data);
		if(root==null) {
			root=newnode;
			return;
		}
	 Queue<Node> q=new LinkedList<>();
	 q.add(root);
	 while(!q.isEmpty()) {
	 Node temp=q.poll();
	 if(temp.left == null) {
		 temp.left=newnode;
		 break;
	 }
	 else {
		 q.add(temp.left);
	 }
	 if(temp.right == null) {
		 temp.right=newnode;
		 break;
	 }
	 else {
		 q.add(temp.right);
	 }
	 }
	}
	
	public void preorder(Node root) {
		if(root !=null) {
			System.out.print(root.data+" ");
			preorder(root.left);
			preorder(root.right);
			
		}
	}
	
	public boolean checkbinary(Node root,long min,long max){
	    if(root== null)
	    {
	        return true;
	    }
	    if(root.data <= min || root.data >= max)
	    {
	        return false;
	    }
	    
	    if(checkbinary(root.left,min,root.data) && checkbinary(root.right,root.data,max)){
	        return true;
	    }
	    return false;
	}
	
	public boolean isValid(Node root){
	    return checkbinary(root,Long.MIN_VALUE,Long.MAX_VALUE);
	}
	
}
public class Main {

	public static void main(String[] args) {
	  Scanner s=new Scanner(System.in);
	  Binarytree obj=new Binarytree();
	  int n=s.nextInt();
	  for(int i=0;i<n;i++) {
		  int val=s.nextInt();
		  obj.insert(val);
	  }
	  System.out.println("pre order Traversal "  );
	obj.preorder(obj.root) ;
	boolean found=obj.isValid(obj.root);
	if(found==true)
	{
	    System.out.println("Valid Binary Search Tree");
	}
	else{
	    System.out.println("Not valid Binary Search Tree");
	}
	  

	}

}


## OUTPUT:

7
10
5
15
3
7
12
18
pre order Traversal 
10 5 3 7 15 12 18
Valid Binary Search Tree
````



