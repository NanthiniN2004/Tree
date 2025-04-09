## Check whether two tree is equal or not

````java[]

package nanthu;
import java.util.*;
import java.lang.*;

class Node{
	int data;
	Node left,right;
	Node (int data){
		this.data=data;
		this.left=null;
		this.right=null;

		}
}
class Tree{
    Node root,left,right;
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
	public void  update(Node root,int ov,int nv) {
		if(root==null) {
			return;
		}
		if(root.data==ov) {
			root.data=nv;
		}
	 update(root.left,ov,nv);
	 update(root.right,ov,nv);
	}
	
	public void delete(int value) {
	    if (root == null) return;

	    if (root.left == null && root.right == null) {
	        if (root.data == value)
	            root = null;
	        return;
	    }

	    Queue<Node> q = new LinkedList<>();
	    q.add(root);

	    Node nodeToDelete = null;
	    Node temp = null;
	    while (!q.isEmpty()) {
	        temp = q.poll();

	        if (temp.data == value) {
	            nodeToDelete = temp;
	        }
	        if (temp.left != null)
	            q.add(temp.left);
	        if (temp.right != null)
	            q.add(temp.right);
	    }
	    if (nodeToDelete != null) {
	        int x = temp.data;
	        deleteNode(temp);       
	        nodeToDelete.data = x;
	    }
	}

	public  void deleteNode( Node del) {
	 Queue<Node> q=new LinkedList<>();
	 q.add(root);
	 while(!q.isEmpty()) {
		 Node temp=q.poll();
		 if(temp==del){
			 temp=null;
			 return;
		 }
	if(temp.left != null) {
	 if(temp.left == del) {
		 temp.left=null;
		 return;
	 }
	 else {
		 q.add(temp.left);
	 }
	}
	if(temp.right !=null) {
	 if(temp.right == del) {
		 temp.right=null;
		 return;
	 }
	 else {
		 q.add(temp.right);
	 }
	}
	 }
	}
	
	public int height(Node root) {
		if(root==null) {
			return -1;
		}
		int heightofleft=height(root.left);
		int heightofright=height(root.right);
		int heightoftree =Math.max(heightofleft, heightofright)+1;
		return heightoftree;
	}
	
	public void inorder(Node root) {
		if(root!=null) {
		inorder(root.left);
		System.out.print(root.data+" ");
		inorder(root.right);
	}
	}
	public void preorder(Node root) {
		if(root!=null) {
	
		System.out.print(root.data+" ");
		preorder(root.left);
		preorder(root.right);
	}
	}
	public void postorder(Node root) {
		if(root!=null) {
		postorder(root.left);
		postorder(root.right);
		System.out.print(root.data+" ");
	
	}
	}
	public void levelOrder(Node root) {
		if(root== null) {
			return;
		}
		Queue<Node> q=new LinkedList<>();
		q.add(root);
		while(!q.isEmpty()) {
			Node temp=q.poll();
			System.out.print(temp.data+" ");
			if(temp.left !=null) {
				q.add(temp.left);
			}
			if(temp.right != null) {
				q.add(temp.right);
			}
		}
	}
	
	public void MaxValue(Node root) {
		if(root== null) {
			return;
		}
		Queue<Node> q=new LinkedList<>();
		q.add(root);
		int level=0;
		
		while(!q.isEmpty()) {
			int n=q.size();
			int max=Integer.MIN_VALUE;
			for(int i=0;i<n;i++) {
			Node temp=q.poll();
			max=Math.max(temp.data, max);
			if(temp.left !=null) {
				q.add(temp.left);
			}
			if(temp.right != null) {
				q.add(temp.right);
			}
		}
			System.out.println("LEVEL " + level +"Maximum value is: " +max);
			level++;
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
		Tree obj=new Tree();
		obj.insert(50);
		obj.insert(25);
		obj.insert(75);
		obj.insert(12);
		obj.insert(37);
		obj.insert(62);
		obj.insert(87);
		
		Tree obj1=new Tree();
		obj1.insert(50);
		obj1.insert(25);
		obj1.insert(75);
		obj1.insert(12);
		obj1.insert(37);
		obj1.insert(62);
		obj1.insert(87);
		System.out.println("\nInorder Traversal");
		obj.inorder(obj.root);
		System.out.println("\npreorder Traversal");
		obj.preorder(obj.root);
		System.out.println("\npostorder Traversal");
		obj.postorder(obj.root);
		System.out.println("\nLevel Order Traversal");
		obj.levelOrder(obj.root);
		System.out.println("\nHeight of the Tree " + obj.height(obj.root) );
		obj.MaxValue(obj.root);
		System.out.println("Compare the Two Binary Tree " + obj.compareTree(obj.root,obj1.root));	    

	}

}

## output:

Inorder Traversal
12 25 37 50 62 75 87 
preorder Traversal
50 25 12 37 75 62 87 
postorder Traversal
12 37 25 62 87 75 50 
Level Order Traversal
50 25 75 12 37 62 87 
Height of the Tree 2
LEVEL 0Maximum value is: 50
LEVEL 1Maximum value is: 75
LEVEL 2Maximum value is: 87
Compare the Two Binary Tree true

````

