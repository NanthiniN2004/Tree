## COUNT THE NODES IN THE TREE
```java[]
package nanthu;

//count the nodes 
import java.util.*;
import java.lang.*;
class TreeNode{
 int value;
 TreeNode left;
 TreeNode right;
 
 TreeNode(int value){
     this.value = value;
     this.left= null;
     this.right= null;

 }
}

class BinaryTree{
 TreeNode root;
 
 public void insert(int data) {
	 TreeNode newnode=new TreeNode(data);
	 if(root==null) {
		 root=newnode;
		 return;
	 }
	 Queue<TreeNode> q=new LinkedList<>();
	 q.add(root);
	 while(!q.isEmpty()) {
		 TreeNode temp=q.poll();
		 if(temp.left == null) {
			 temp.left=newnode;
			 break;
		 }
		 else {
			 q.add(temp.left);
		 }
		 if(temp.right==null) {
			 temp.right=newnode;
			 break;
		 }
		 else {
			 q.add(temp.right);
		 }
	 }
 }
 
 public int countNodes(TreeNode node){
     if(node==null){
         return 0;
     }
     
     return 1 + countNodes(node.left) + countNodes(node.right);
     
 }

}

public class CountNodes{
 public static void main(String[] args){
     BinaryTree tree = new BinaryTree();
     Scanner s=new Scanner(System.in);
     System.out.println("Enter the number of node you want to add");
     int n=s.nextInt();
     for(int i=0;i<n;i++) {
    	 int val=s.nextInt();
    	 tree.insert( val);
     }
      int nodeCount = tree.countNodes(tree.root);
     
     System.out.println("No of nodes :" + nodeCount);
 }
}

## OUTPUT:
Enter the number of node you want to add
7
1
2
3
4

5
6
7
No of nodes :7

````


