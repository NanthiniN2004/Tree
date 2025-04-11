## CHECK THE TREE IS BALANCE OR NOT
````java[]

package nanthu;
 class Node{
	 int data;
	 Node left,right;
	 Node(int data){
		 this.data=data;
		 this.left=0.null;
		 this.right=null;
		 }
 }
 class Balanced{
	 Node root;
	  public int height(Node root) {
		  if(root==null) {
			  return -1;
		  }
		  else {
			   return 1+Math.max(height(root.left), height(root.right));
		  }
	  }
	  public void insert(int key) {
	        root = insertRec(root, key);
	    }

	  public Node insertRec(Node root,int data) {
		  Node newnode=new Node(data);
		  if(root==null) {
			  root=newnode;
		  }
		  if(data<root.data) {
			  root.left=insertRec(root.left,data);
		  }
		  else if(data>root.data) {
			  root.right=insertRec(root.right,data);
		  }
		  else {
			  return root;
		  }
		  height(root);
		  int balance=checkbalance(root);
		  if(balance> 1 && data<root.left.data) {
			  return rightRotation(root);
		  }
		  if (balance < -1 && data> root.right.data)
	            return leftRotation(root);

	       
	        if (balance > 1 && data > root.left.data) {
	            root.left = leftRotation(root.left);
	            return rightRotation(root);
	        }
	        if (balance < -1 && data < root.right.data) {
	            root.right = rightRotation(root.right);
	            return leftRotation(root);
	        }
	        return root;
	  }
	  public Node leftRotation(Node temp) {
		     Node newroot=temp.right;
		     Node transfer=newroot.left;
		     newroot.left=temp;
		     temp.right=transfer;
		     height(temp);
		     height(newroot);
		     return newroot;		     	  
	  }
	  public Node rightRotation(Node temp) {
		     Node newroot=temp.left;
		     Node transfer=newroot.right;
		     newroot.right=temp;
		     temp.left=transfer;
		     height(newroot);
		     height(temp);
		     return newroot;		     	  
	  }
	  public int checkbalance(Node node) {
	        return (node == null) ? 0 : height(node.left) - height(node.right);
	    }
        public void inorder(Node root) {
        	if(root!= null) {
        	inorder(root.left);
        	System.out.print(root.data+" ");
        	inorder(root.right);
        }
        }
 }
public class Balancedtree {

	public static void main(String[] args) {
       Balanced tree=new Balanced();
       tree.insert(10);
       tree.insert(20);
       tree.insert(30);
       tree.insert(40);
       tree.insert(50);
       tree.insert(25);
       System.out.println("Inorder Traversal After Constructing AVL Tree");
       tree.inorder(tree.root);
	}

}


## OUTPUT:

Inorder Traversal After Constructing AVL Tree
10 20 25 30 40 50

`````

