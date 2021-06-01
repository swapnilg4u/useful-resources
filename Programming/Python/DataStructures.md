# All Data Structures at one place
1. [Linked Lists](https://github.com/swapnilg4u/useful-resources/blob/main/Programming/Python/DataStructures.md#linked-lists)
2. [Doubly Linked Lists](https://github.com/swapnilg4u/useful-resources/blob/main/Programming/Python/DataStructures.md#doubly-linked-lists-)

## Linked Lists

```
# Basic Linked List Operations - Initialize, Add(front,back,inbetween), Delete, Print, Reverse

# Node class
class Node:

    # Function to initialise the node object
    def __init__(self, data):
        self.data = data  # Assign data
        self.next = None  # Initialize next as null


# Linked List class contains a Node object
class LinkedList:

    # Function to initialize head
    def __init__(self):
        self.head = None

# This function prints contents of linked list starting from head
    def printList(self):
        temp = self.head
        while (temp):
            print(temp.data)
            temp = temp.next

# Function to insert a new node at the beginning
    def push(self, new_data):

        # 1 & 2: Allocate the Node &
        #	 Put in the data
        new_node = Node(new_data)

        # 3. Make next of new Node as head
        new_node.next = self.head

        # 4. Move the head to point to new Node
        self.head = new_node


# Inserts a new node after the given prev_node.


    def insertAfter(self, prev_node, new_data):

        # 1. check if the given prev_node exists
        if prev_node is None:
            print("The given previous node must inLinkedList.")
            return

        # 2. create new node &
        #	 Put in the data
        new_node = Node(new_data)

        # 4. Make next of new Node as next of prev_node
        new_node.next = prev_node.next

        # 5. make next of prev_node as new_node
        prev_node.next = new_node

# Appends a new node at the end.
    def append(self, new_data):

        # 1. Create a new node
        # 2. Put in the data
        # 3. Set next as None
        new_node = Node(new_data)

        # 4. If the Linked List is empty, then make the
        # new node as head
        if self.head is None:
            self.head = new_node
            return

        # 5. Else traverse till the last node
        last = self.head
        while (last.next):
            last = last.next

        # 6. Change the next of last node
        last.next = new_node

# Deletes a given node
    def delete(self, new_data):
        dele = self.head
        if dele.data == new_data:
            self.head = dele.next
            temp = None
            return

        while dele:
            if dele.data == new_data:
                print(f'\n{dele.data} found and is being deleted')
                break
            prev = dele
            dele = dele.next
        prev.next = dele.next

# Reverse the Linked List
    def reverse(self):
        llist.printList()

        current = self.head
        prev = None
        while current:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
        self.head = prev


# Code execution starts here
if __name__ == '__main__':

    # Start with the empty list
    llist = LinkedList()

    # Insert 6. So linked list becomes 6->None
    llist.append(6)

    # Insert 7 at the beginning. So linked list becomes 7->6->None
    llist.push(7)

    # Insert 1 at the beginning. So linked list becomes 1->7->6->None
    llist.push(1)

    # Insert 4 at the end. So linked list becomes 1->7->6->4->None
    llist.append(4)

    # Insert 8, after 7. So linked list becomes 1 -> 7-> 8-> 6-> 4-> None
    llist.insertAfter(llist.head.next, 8)

    # Delete 6. So linked list becomes 1 -> 7-> 8-> 4-> None
    llist.delete(6)

    # Reverse the Linked List
    llist.reverse()

    print('Created linked list is:')
    llist.printList()

```

## Doubly Linked Lists <a id=doubly-linked-list />
```
# A complete working Python program to demonstrate all insertion methods

# A linked list node
class Node:

    # Constructor to create a new node
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

# Class to create a Doubly Linked List


class DoublyLinkedList:

    # Constructor for empty Doubly Linked List
    def __init__(self):
        self.head = None

    # Given a reference to the head of a list and an integer, inserts a new node on the front of list
    def push(self, new_data):

        # 1. Allocates node
        # 2. Put the data in it
        new_node = Node(new_data)

        # 3. Make next of new node as head and previous as None (already None)
        new_node.next = self.head

        # 4. change prev of head node to new_node
        if self.head is not None:
            self.head.prev = new_node

        # 5. move the head to point to the new node
        self.head = new_node

    # Given a node as prev_node, insert a new node after the given node
    def insertAfter(self, prev_node, new_data):

        # 1. Check if the given prev_node is None
        if prev_node is None:
            print("the given previous node cannot be NULL")
            return

        # 2. allocate new node
        # 3. put in the data
        new_node = Node(new_data)

        # 4. Make net of new node as next of prev node
        new_node.next = prev_node.next

        # 5. Make prev_node as previous of new_node
        prev_node.next = new_node

        # 6. Make prev_node ass previous of new_node
        new_node.prev = prev_node

        # 7. Change previous of new_nodes's next node
        if new_node.next:
            new_node.next.prev = new_node

    # Given a reference to the head of DLL and integer, appends a new node at the end
    def append(self, new_data):

        # 1. Allocates node
        # 2. Put in the data
        new_node = Node(new_data)

        # 3. This new node is going to be the last node, so make next of it as None (It already is initialized as None)

        # 4. If the Linked List is empty, then make the new node as head
        if self.head is None:
            self.head = new_node
            return

        # 5. Else traverse till the last node
        last = self.head
        while last.next:
            last = last.next

        # 6. Change the next of last node
        last.next = new_node

        # 7. Make last node as previous of new node
        new_node.prev = last

        return

    # This function prints contents of linked list starting from the given node
    def printList(self, node):

        print("\nTraversal in forward direction")
        while node:
            print(node.data)
            last = node
            node = node.next

        print("\nTraversal in reverse direction")
        while last:
            print(last.data)
            last = last.prev

# Driver program to test above functions


# Start with empty list
llist = DoublyLinkedList()

# Insert 6. So the list becomes 6->None
llist.append(6)

# Insert 7 at the beginning. So linked list becomes 7->6->None
llist.push(7)

# Insert 1 at the beginning. So linked list becomes 1->7->6->None
llist.push(1)

# Insert 4 at the end. So linked list becomes 1->7->6->4->None
llist.append(4)

# Insert 8, after 7. So linked list becomes 1->7->8->6->4->None
llist.insertAfter(llist.head.next, 8)

print("Created DLL is: ")
llist.printList(llist.head)
```
