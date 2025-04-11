## 1) INSERT, UPDATE,READ,DELETE THE ELEMENT IN BINARY SEARCH TREE 
## 2) FIND THE MINIMUM AND MAXIMUM VALUE IN BINARY SEARCH TREE
## 3) CHECK THE ELEMENT IS PRESENT OR NOT
## 4) PRINT DATA IN ASCENDING ORDER AND DECENDING ORDER
````java[]

package nanthu;
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
class Operation{
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
	public Node delete(Node root,int val)
	{
		if(root.data >val) {
			root.left=delete(root.left,val);
		}
		else if(root.data < val) {
			root.right=delete(root.right,val);
		}
		else
		{
			if(root.left ==null)
			{
				return root.right;
			}
			else if(root.right ==null) {
				return root.left;
			}
			root.data=minimum(root.right);
			root.right=delete(root.right,root.data);
		}
		return root;
	}
	public boolean search(Node root,int key) {
		if(root==null) {
			return false;
		}
		else
		{
			if(root.data==key) {
				return true;
			}
			else if(root.data >key) {
				 return search(root.left,key);
			}
			else
			{
				return search(root.right,key);
			}
		}
	}
	public void decending(Node root) {
		if(root !=null) {
			decending(root.right);
			System.out.print(root.data+" ");
			decending(root.left);
		}
	}
	
	public void inorder(Node root) {
		if(root !=null) {
			inorder(root.left);
			System.out.print(root.data+" ");
			inorder(root.right);
		}
	}
	public int minimum(Node root) {
		if(root==null) {
			return 0;
		}
		while(root.left != null) {
			root=root.left;
		}
		return root.data;
	}
	public int maximum(Node root) {
		if(root==null) {
			return 0;
		}
		while(root.right != null) {
			root=root.right;
		}
		return root.data;
	}
	public void  update(Node root,int ov,int nv) {
		
		    if (search(root, ov)) {
		        root = delete(root, ov);
		        root = insert(root, nv);
		    } else {
		        System.out.println("Value not found in BST");
		    }

	 
	 
	}
}
public class BinarySearchTree {

	public static void main(String[] args) {
		Scanner s=new Scanner(System.in);
		Operation obj=new Operation();
		int n=s.nextInt();
        for(int i=0;i<n;i++) {
        	int val=s.nextInt();
        	obj.insertrev(val);
        }
        System.out.println("Inorder Traversal");
        obj.inorder(obj.root);
        System.out.println("\nEnter the element you want search");
        int key=s.nextInt();
        boolean found=obj.search(obj.root,key);
        if(found) {
        	System.out.println(key +" is found ");
        }
        else
        {
        	System.out.println(key +" is not found");
        }
        
        System.out.println("Ascending Order of the Element");
        obj.inorder(obj.root);
        System.out.println("\nDecending Order of the Element");
        obj.decending(obj.root);
        
        System.out.println("\nMaximum Value of the Binary Search Tree: "+obj.maximum(obj.root));
        
        System.out.println("Manimum Value of the Binary Search Tree: "+      obj.minimum(obj.root));
        System.out.println("Enter the element you want delete");
        int del=s.nextInt();
        obj.delete(obj.root,del);
        
        System.out.println("After Deletion");
        obj.inorder(obj.root);
        
        obj.update(obj.root,40,55);
        System.out.println("\nAfter update the value");
        obj.inorder(obj.root);
   
	}
	

}

## OUTPUT:

7
50
30
70
20
40
60
80
Inorder Traversal
20 30 40 50 60 70 80 
Enter the element you want search
20
20 is found 
Ascending Order of the Element
20 30 40 50 60 70 80 
Decending Order of the Element
80 70 60 50 40 30 20 
Maximum Value of the Binary Search Tree: 80
Manimum Value of the Binary Search Tree: 20
Enter the element you want delete
70
After Deletion
20 30 40 50 60 80
After update the value
20 30 50 55 60 80

````
