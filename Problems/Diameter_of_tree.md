## WRITE A JAVA PROGRAM FIND THE DIAMETER OF THE BINARY TREE

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
	int dia=0;
	
 public int findheight(Node root) {
		if(root==null) {
			return 0;
		}
		int leftheight=findheight(root.left);
		int rightheight=findheight(root.right);
		dia=Math.max(dia, leftheight+rightheight);
		return 1+Math.max(leftheight, rightheight);
		
	}
	public int diameter(Node root) {
		findheight(root);
		return dia;
	}
}
public class Main {

	public static void main(String[] args) {
	  Scanner s=new Scanner(System.in);
	  Binarytree obj=new Binarytree();
	 // Binarytree obj1=new Binarytree();
	  System.out.println("Enter how many element you want add tree 1 ");
	  int n=s.nextInt();
	  System.out.println("Enter the element ");
	  for(int i=0;i<n;i++) {
		  int val=s.nextInt();
		 
		  obj.insertrev(val);
	  }
	  
	  System.out.println("pre order Traversal "  );
	obj.preorder(obj.root) ;
     
     System.out.println("\nDiameter of the tree: "+ obj.diameter(obj.root));

	}

}


OUTPUT:

Enter how many element you want add tree 1 
5
Enter the element 
1
2
3
4
5
pre order Traversal 
1 2 3 4 5 
Diameter of the tree: 4

`````
