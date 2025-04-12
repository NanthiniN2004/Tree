## WRITE A JAVA PROGRAM FIND THE MIRROR OF THE TREE

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
	
	public void inorder(Node root) {
		if(root !=null) {
		    	inorder(root.left);
			System.out.print(root.data+" ");
		
			inorder(root.right);
			
		}
	}
	int dia=0;
	
 public void mirror(Node root)
 {
     if(root==null)
     {
         return;
     }
     else{
         Node temp;
         mirror(root.left);
         mirror(root.right);
         temp=root.left;
         root.left=root.right;
         root.right=temp;
     }
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
	  
	  System.out.println("in order Traversal "  );
	obj.inorder(obj.root) ;
      obj.mirror(obj.root);
     System.out.println("\nMirror of the tree: ");
    obj.inorder(obj.root);

	}

}

OUTPUT:

Enter how many element you want add tree 1 
7
Enter the element 
10
4
17
3
7
12
15
in order Traversal 
3 4 7 10 12 15 17 
Mirror of the tree: 
17 15 12 10 7 4 3

````

