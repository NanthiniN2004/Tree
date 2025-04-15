## MERGE TWO BINARY TREE IN JAVA

````java[]

package nanthuu;
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
public class Main2 {
	Node root;
	Node insert(Node root, int val) {
	        if (root == null) return new Node(val);
	        if (val < root.data) root.left = insert(root.left, val);
	        else root.right = insert(root.right, val);
	        return root;
	    }
 public void inorder(Node root,List<Integer> list) {
	 if(root !=null) {
		 inorder(root.left,list);
		 list.add(root.data);
		 inorder(root.right,list);
		 
	 }
 }
 
 List<Integer> mergedarray(List<Integer> list1,List<Integer> list2)
 {
	 List<Integer> merged=new ArrayList<>();
	 int i=0,j=0;
	 while(i< list1.size()  && j<list2.size())
	 {
		 if(list1.get(i)<list2.get(j)) {
			 merged.add(list1.get(i++));
		 }
		 else {
			 merged.add(list2.get(j++));
		 }
	 }
	 while(i<list1.size()) {
		 merged.add(list1.get(i++));
	 }
	 while(j<list2.size())
	 {
		 merged.add(list2.get(j++));
	 }
	 return merged;
	 
 }
 
 public Node construct(List<Integer> list,int start,int end)
 {
	 if(start>end)
	 {
		 return null;
	 }
	 int mid=(start+end)/2;
	 Node root=new Node(list.get(mid));
	 root.left=construct(list,start,mid-1);
	 root.right=construct(list,mid+1,end);
	 return root;
 }
 void printInorder(Node root) {
     if (root == null) return;
     printInorder(root.left);
     System.out.print(root.data + " ");
     printInorder(root.right);
 }
 
 public Node Mergebst(Node root1,Node root2)
 {
	 List<Integer> list1=new ArrayList<>();
	 List<Integer> list2=new ArrayList<>();
	 inorder(root1,list1);
	 inorder(root2,list2);
	List<Integer> mergedlist= mergedarray(list1,list2);
	 return construct(mergedlist,0,mergedlist.size()-1);
 }
	public static void main(String[] args) {
	     Scanner s=new Scanner(System.in);
	     Node root1=null,root2=null;
	     Main2 obj=new Main2();
	     System.out.println("Enter the element you want add tree 1");
	     int n=s.nextInt();
	     System.out.println("Enter the element");
	     for(int i=0;i<n;i++) {
	    	 int val=s.nextInt();
	    	root1= obj.insert(root1,val);
	     }
	     System.out.println("Enter the element you want add tree 2");
	     int n1=s.nextInt();
	     System.out.println("Enter the element");
	     for(int i=0;i<n1;i++) {
	    	 int val1=s.nextInt();
	    	root2= obj.insert(root2,val1);
	     }
	     System.out.println("merged Two Binary Search Tree");
	     Node m=obj.Mergebst(root1,root2);
         obj.printInorder(m);
	}

}

OUTPUT:

Enter the element you want add tree 1
3
Enter the element
3
1
5
Enter the element you want add tree 2
3
Enter the element
4
2
6
merged Two Binary Search Tree
1 2 3 4 5 6

`````
