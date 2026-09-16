# Ex6 Right Rotation LinkedList
## DATE:16.7.2026
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
Read n values to build the linked list and read k. Find the length of the list and reach the last node. Make the list circular by connecting last node to head. Move length − (k % length) steps to find new tail. Break the circle and print the list from the new head.
## Program:
```
/*
Program to  Right Rotation LinkedList
Developed by: MERLIN M
RegisterNumber: 212225240084 
*/
import java.util.Scanner;

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class prog {
    public static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0)
            return head;

        Node temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        temp.next = head;

        int stepsToNewHead = length - k % length;
        Node newTail = head;
        for (int i = 1; i < stepsToNewHead; i++) {
            newTail = newTail.next;
        }

        Node newHead = newTail.next;

        newTail.next = null;

        return newHead;
    }

    public static void printList(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n <= 0) {
            sc.close();
            return;
        }

        Node head = new Node(sc.nextInt());
        Node tail = head;
        for (int i = 1; i < n; i++) {
            tail.next = new Node(sc.nextInt());
            tail = tail.next;
        }

        int k = sc.nextInt();

        head = rotateRight(head, k);

        System.out.print("LinkedList: ");
        printList(head);

        sc.close();
    }
}
```

## Output:
<img width="793" height="196" alt="image" src="https://github.com/user-attachments/assets/2e18622e-e4b2-4f7d-a39d-9c40f572c043" />



## Result:
Thus, the C program to perfom right rotation on linked list is implemented successfully.
