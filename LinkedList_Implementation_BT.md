## LINKED LIST IMPLEMENTION USING BINARY TREE IN JAVA

````java[]

package nanthuu;
import java.util.*;

class Node {
    int data;
    Node left, right;

    Node(int data) {
        this.data = data;
        left = right = null;
    }
}

class Binarytree {
    Node root;

    public void insert(int data) {
        Node newnode = new Node(data);

        if (root == null) {
            root = newnode;
            return;
        }

        Queue<Node> q = new LinkedList<>();
        q.add(root);

        while (!q.isEmpty()) {
            Node temp = q.poll();

            if (temp.left == null) {
                temp.left = newnode;
                break;
            } else {
                q.add(temp.left);
            }

            if (temp.right == null) {
                temp.right = newnode;
                break;
            } else {
                q.add(temp.right);
            }
        }
    }

    public void inorder(Node root) {
        if (root != null) {
            inorder(root.left);
            System.out.print(root.data + " ");
            inorder(root.right);
        }
    }
}

public class Main1 {
    public static void main(String[] args) {
        Binarytree obj = new Binarytree();
        Scanner s = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = s.nextInt();
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            int val = s.nextInt();
            obj.insert(val);
        }
        System.out.println("Inorder traversal:");
        obj.inorder(obj.root);
        s.close();
    }
}


    OUTPUT:

Enter number of elements: 7
Enter elements:
10
20
30
40
50
60
70
Inorder traversal:
40 20 50 10 60 30 70

````
