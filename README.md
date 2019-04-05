Binary Tree (Java ) random generations

1. Generated and insert random binary tree
2. Find heidht tree


Redone by LinkClink





Original links:
https://www.javatpoint.com/program-to-find-the-maximum-depth-or-height-of-a-tree
http://www.java2novice.com/java-interview-programs/height-of-binary-search-tree-bst/



Code::

/* Republic by LinkClink */

import java.util.Random;

class Node
{
    public int value;
    public Node left;
    public Node right;
}

class Tree
{

    public Node insert(Node root, int v)
    {
        if (root == null)
        {
            root = new Node();
            root.value = v;
        }
        else if (v < root.value) root.left = insert(root.left, v);
        else root.right = insert(root.right, v);

        return root;
    }

    public void traverse(Node root)
    {
        if (root == null) return;

        traverse(root.left);
        traverse(root.right);
    }

    public int findHeight(Node temp)
    {

            int leftHeight = 0, rightHeight = 0;

            if(temp.left != null)
                leftHeight = findHeight(temp.left);

            if(temp.right != null)
                rightHeight = findHeight(temp.right);

            int max = (leftHeight > rightHeight) ? leftHeight : rightHeight;

            return (max + 1);
    }
}

class BinarySearchTree
{
    public static void main(String[] args)
    {
        int c , b , i=0;
        int aver = 0;

        // Tree size
        int plus_size=10;
        int SIZE = 100;
        int[] a = new int[SIZE];

        for (c = 1; c<= 10000; c++)
        {
            System.out.print(SIZE + ";");

            for(b = 1; b<=3; b++)
            {
                Node root = null;
                Tree bst = new Tree();

                Random random = new Random();

                for (i = 0; i < SIZE; i++)
                {
                    a[i] = random.nextInt(SIZE);
                    //System.out.print(a[i]+"\n");
                }

                for (i = 0; i < SIZE; i++) root = bst.insert(root, a[i]);

                bst.traverse(root);

                aver += bst.findHeight(root);
                System.out.print(bst.findHeight(root)+";");

            }
            aver = aver/3;
            System.out.print(aver +"\n");

            SIZE += plus_size;
            a = new int[SIZE];

            aver = 0;
        }
    }
