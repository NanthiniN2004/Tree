## WRITE A JAVA PROGRAM FIND THE MAXIMUM ELEMENT IN A TREE
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
	public Node insert(Node root,int data) {
		Node newnode=new Node(data);
		if(root== null) {
			return newnode;
		}
		if(root.data>data) {
			root.left=insert(root.left,data);
		}
		else
		{
			root.right=insert(root.right,data);
		}
		return root;
	}
	public void insertrev(int data) {
	this.root=	insert(this.root,data);
	}
	
	public void preorder(Node root) {
		if(root !=null) {
			System.out.print(root.data+" ");
			preorder(root.left);
			preorder(root.right);
			
		}
	}
	public int max(Node root) {
		if(root ==null) {
			return 0;
		}
		while(root.right !=null) {
			root=root.right;
		}
		return root.data;
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
	  System.out.println("/nMaximum value in the tree "+ obj.max(obj.root));

	}

}

OUTPUT:

6
50
30
70
20
40
60
pre order Traversal 
50 30 20 40 70 60 Maximum value in the tree 70

````

