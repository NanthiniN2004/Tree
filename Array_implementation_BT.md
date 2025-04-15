## ARRAY IMPLEMENTATION USING TREE IN JAVA

````java[]
package nanthuu;
import java.util.*;
public class Main {
    int[] a;
    int size;
    Main(int capacity)
    {
    	a=new int[capacity];
    	size=0;
    }
    public void insert(int data)
    {
    	if(size<a.length)
    	{
    		a[size]=data;
    		size++;
    	}
    	else 
    	{
    		System.out.println("Array full");
    	}
    }
    
    public void display()
    {
    	for(int i=0;i<size;i++) {
    		System.out.print(a[i] +" ");
    	}
    }
    public int lefttree(int i)
    {
    	int left=(2*i)+1;
    	if(left<size)
    	{
    		return a[left];
    	}
    	return -1;
    }
    
    public int righttree(int i)
    {
    	int right=(2*i)+2;
    	if(right<size) {
    		return a[right];
    	}
    	return -1;
    }
    
    public int parent(int i)
    {
    	if(i==0 || i>=size)
    	{
    		return -1;
    	}
    	int parent=(i-1)/2;
    	return a[parent];
    }
	public static void main(String[] args) {
	    Scanner s=new Scanner(System.in);
	    Main obj=new Main(15);
	    for(int i=0;i<7;i++) {
	    	int val=s.nextInt();
	    	obj.insert(val);
	    }
	    obj.display();
	    System.out.println("left child of the index 0: "+ obj.lefttree(0));
	    System.out.println("right child of the index 0: "+ obj.righttree(0));
	    System.out.println("parent of the tree "+ obj.parent(2));
	    
	}

}

OUTPUT:

1
2
3
4
5
6
7
1 2 3 4 5 6 7
left child of the index 0: 2
right child of the index 0: 3
parent of the tree 1

````


