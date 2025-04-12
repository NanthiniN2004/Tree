## WRITE A JAVA PROGRAM FIND THE DIFFERENCE BETWEEN ODD LEVEL SUM AND EVEN LEVEL SUM
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
	public int difference(Node root)
	{
	    if(root==null)
	    {
	        return 0;
	    }
	    int level=1;
	   
	    int evensum=0;
	    int oddsum=0;
	    Queue<Node> q=new LinkedList<>();
	    q.add(root);
	    while(!q.isEmpty()){
	         int levelsum=0;
	        int n=q.size();
	        for(int i=0;i<n;i++){
	             Node temp=q.poll();
	            if(level %2==1)
	            {
	                oddsum+=temp.data;
	            }
	            else{
	                evensum+=temp.data;
	            }
	            if(temp.left !=null)
	            {
	                q.add(temp.left);
	            }
	            if(temp.right !=null){
	                q.add(temp.right);
	            }
	        }
	        level++;
	        
	    }
	    return oddsum-evensum;
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
      System.out.println("\nDifference between sum of odd level and sum of even level "+obj.difference(obj.root));

	}

}

OUTPUT:

Enter how many element you want add tree 1 
9
Enter the element 
5
2
6
1
4
8
3
7
9
in order Traversal 
1 2 3 4 5 6 7 8 9
 Difference between sum of odd level and sum of even level -9

````

