## WRITE A JAVA PROGRAM CHECK WHETHER TREE IS IDENTICAL OR NOT

````JAVA[]


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
	
 public boolean compareTree(Node root1, Node root2) {
		if(root1 == null && root2 ==null) {
			return true;
		}
		if(root1 == null || root2 ==null) {
			return false;
		}
		return (root1.data == root2.data) && (compareTree(root1.left,root2.left)) && (compareTree(root1.right,root2.right));
	}
}
public class Main {

	public static void main(String[] args) {
	  Scanner s=new Scanner(System.in);
	  Binarytree obj=new Binarytree();
	  Binarytree obj1=new Binarytree();
	  System.out.println("Enter how many element you want add tree 1 ");
	  int n=s.nextInt();
	  System.out.println("Enter the element ");
	  for(int i=0;i<n;i++) {
		  int val=s.nextInt();
		 
		  obj.insertrev(val);
	  }
	  System.out.println("Enter how many element you want add in Tree 2 ");
	  int n1=s.nextInt();
	  System.out.println("Enter the element ");
	  for(int i=0;i<n1;i++) {
		  int val1=s.nextInt();
		 
		  obj1.insertrev(val1);
	  }
	  System.out.println("pre order Traversal "  );
	obj.preorder(obj.root) ;
     	System.out.println("\nCompare the Two Binary Tree is Identical or not:  ");
     	boolean found=obj.compareTree(obj.root,obj1.root);
	  if(found==true)
	  {
	      System.out.println("Both tree is Identical Tree");
	  }
	  else{
	      System.out.println("Both tree is not identical tree");
	  }

	}

}


## OUTPUT:

Enter how many element you want add tree 1 
3
Enter the element 
1
2
3
Enter how many element you want add in Tree 2 
3
Enter the element 
2
3
4
pre order Traversal 
1 2 3 
Compare the Two Binary Tree is Identical or not:  
Both tree is not identical tree
