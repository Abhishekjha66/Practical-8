import java.util.Scanner; 
 
class Node { 
    int data; 
    Node left, right; 
 
    public Node(int item) {         data = item;         left = right = null; 
    } 
} 
 
class BinarySearchTree { 
    Node root; 
 
    BinarySearchTree() {         root = null; 
    } 
 
    void insert(int key) {         root = insertRec(root, key); 
    } 
 
    Node insertRec(Node root, int key) {         if (root == null) {             root = new Node(key);             return root; 
        }         if (key < root.data)             root.left = insertRec(root.left, key);         else if (key > root.data)             root.right = insertRec(root.right, key);         return root; 
    } 
 
    void inorder() {         inorderRec(root); 
    } 
 
    void inorderRec(Node root) {         if (root != null) {             inorderRec(root.left);             System.out.print(root.data + " ");             inorderRec(root.right); 
        } 
    } 
 
    void preorder() {         preorderRec(root); 
    } 
 
    void preorderRec(Node root) {         if (root != null) { 
            System.out.print(root.data + " ");             preorderRec(root.left);             preorderRec(root.right); 
        } 
    } 
 
    void postorder() {         postorderRec(root); 
    } 
 
    void postorderRec(Node root) {         if (root != null) {             postorderRec(root.left);             postorderRec(root.right);             System.out.print(root.data + " "); 
        } 
    } 
 
    boolean search(int key) {         return searchRec(root, key); 
    } 
 
    boolean searchRec(Node root, int key) {         if (root == null)             return false;         if (root.data == key)             return true;         if (root.data < key)             return searchRec(root.right, key);         return searchRec(root.left, key); 
    } 
} 
 
public class Main { 
    public static void main(String[] args) {         Scanner scanner = new Scanner(System.in); 
        BinarySearchTree bst = new BinarySearchTree();         int[] elements = {6, 9, 5, 2, 8, 15, 24, 14, 7, 8, 5, 2};         for (int element : elements) {             bst.insert(element); 
        }         char choice;         do { 
            System.out.println("\nBinary Search Tree Operations:"); 
            System.out.println("1. Traverse in Inorder"); 
            System.out.println("2. Traverse in Preorder"); 
            System.out.println("3. Traverse in Postorder"); 
            System.out.println("4. Search for element"); 
            System.out.println("5. Exit"); 
 
            System.out.println("Enter your choice:"); 
            int option = scanner.nextInt();             switch (option) {                 case 1: 
                    System.out.print("Inorder traversal: ");                     bst.inorder();                     break;                 case 2: 
                    System.out.print("Preorder traversal: ");                     bst.preorder();                     break;                 case 3: 
                    System.out.print("Postorder traversal: ");                     bst.postorder();                     break;                 case 4: 
                    System.out.println("Enter element to search:");                     int key = scanner.nextInt();                     if (bst.search(key)) 
                        System.out.println(key + " found in the BST.");                     else 
                        System.out.println(key + " not found in the BST.");                     break;                 case 5: 
                    System.out.println("Exiting...");                     System.exit(0);                     break;                 default: 
                    System.out.println("Invalid choice!"); 
            } 
            System.out.println("\nDo you want to continue? (Y/N)");             choice = scanner.next().charAt(0);         } while (choice == 'Y' || choice == 'y');         scanner.close(); 
    } 
} 
