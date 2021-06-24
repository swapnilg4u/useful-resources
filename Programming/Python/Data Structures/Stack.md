# Stack

A Stack is also called Last-In-First-Out (LIFO)

## Stack as an ADT
> A list with restrictions that insertion and deletion can be performed only from one end, called the top.

## Operations

<table>
  <thead>
    <tr>
      <th>Sr. No.</th>
      <th>Operation</th>
      <th>Time Complexity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1.</td>
      <td>Push(x)</td>
      <td rowspan='4'>Constant Time O(1)</td>
    </tr>
    <tr>
      <td>2.</td>
      <td>Pop()</td>
    </tr>
    <tr>
      <td>3.</td>
      <td>Top()</td>
    </tr>
    <tr>
      <td>4.</td>
      <td>Isempty()</td>
    </tr>
  </tbody>
</table>

Some Applications:-
1. Execution of function calls / Recursion
2. Undo operation of an editor
3. Balancing Brackets in compilers

We can implement stack using
1. [Arrays](#arrays)
2. [Linked Lists](#llists)
3. [Inbuilt Python Modules](#modules)

## ARRAY IMPLEMENTATION OF STACK (LISTS) <a id="arrays" />
```
stack = []

stack.append('a')
stack.append('b')
stack.append('c')

print(stack)

print('\nElements popped from stack:')
print(stack.pop())
print(stack.pop())
print(stack.pop())
 
print('\nStack after elements are popped:')
print(stack)
 ```

## LINKED LIST IMPLEMENTATION OF STACK <a id="llists" />
```
class Node:
   def __init__(self, value):
      self.value = value
      self.next = None
 
class Stack:
    
   # Initializing a stack.
   # Use a dummy node, which is
   # easier for handling edge cases.
   def __init__(self):
      self.head = Node("head")
      self.size = 0
 
   # String representation of the stack
   def __str__(self):
      cur = self.head.next
      out = ""
      while cur:
         out += str(cur.value) + "->"
         cur = cur.next
      return out[:-3]  
 
   # Get the current size of the stack
   def getSize(self):
      return self.size
    
   # Check if the stack is empty
   def isEmpty(self):
      return self.size == 0
    
   # Get the top item of the stack
   def peek(self):
       
      # Sanitary check to see if we
      # are peeking an empty stack.
      if self.isEmpty():
         raise Exception("Peeking from an empty stack")
      return self.head.next.value
 
   # Push a value into the stack.
   def push(self, value):
      node = Node(value)
      node.next = self.head.next
      self.head.next = node
      self.size += 1
      
   # Remove a value from the stack and return.
   def pop(self):
      if self.isEmpty():
         raise Exception("Popping from an empty stack")
      remove = self.head.next
      self.head.next = self.head.next.next
      self.size -= 1
      return remove.value
 
# Driver Code
if __name__ == "__main__":
   stack = Stack()
   for i in range(1, 11):
      stack.push(i)
   print(f"Stack: {stack}")
 
   for _ in range(1, 6):
      remove = stack.pop()
      print(f"Pop: {remove}")
   print(f"Stack: {stack}")
```

## SOME PYTHON INBUILT MODULES FOR STACK <a id="modules" />
### Using deque from collections
```
from collections import deque
 
stack = deque()
 
# append() function to push
# element in the stack
stack.append('a')
stack.append('b')
stack.append('c')
 
print('Initial stack:')
print(stack)
 
# pop() fucntion to pop
# element from stack in
# LIFO order
print('\nElements poped from stack:')
print(stack.pop())
print(stack.pop())
print(stack.pop())
 
print('\nStack after elements are poped:')
print(stack)
 
# uncommenting print(stack.pop()) 
# will cause an IndexError
# as the stack is now empty
```

### Using queue
```
from queue import LifoQueue
 
# Initializing a stack
stack = LifoQueue(maxsize = 3)
 
# qsize() show the number of elements
# in the stack
print(stack.qsize())
  
# put() function to push
# element in the stack
stack.put('a')
stack.put('b')
stack.put('c')
 
print("Full: ", stack.full())
print("Size: ", stack.qsize())
 
# get() fucntion to pop
# element from stack in
# LIFO order
print('\nElements poped from the stack')
print(stack.get())
print(stack.get())
print(stack.get())
 
print("\nEmpty: ", stack.empty())
```


## Reverse a String or Linked List using STACK
### String -
```
# Python program to reverse a string using stack

# Function to create an empty stack.
# It initializes size of stack as 0
def createStack():
	stack=[]
	return stack

# Function to determine the size of the stack
def size(stack):
	return len(stack)

# Stack is empty if the size is 0
def isEmpty(stack):
	if size(stack) == 0:
		return true

# Function to add an item to stack .
# It increases size by 1
def push(stack,item):
	stack.append(item)

#Function to remove an item from stack.
# It decreases size by 1
def pop(stack):
	if isEmpty(stack): return
	return stack.pop()

# A stack based function to reverse a string
def reverse(string):
	n = len(string)
	
	# Create a empty stack
	stack = createStack()

	# Push all characters of string to stack
	for i in range(0,n,1):
		push(stack,string[i])

	# Making the string empty since all
	#characters are saved in stack
	string=""

	# Pop all characters of string and
	# put them back to string
	for i in range(0,n,1):
		string+=pop(stack)
		
	return string
	
# Driver program to test above functions
string="GeeksQuiz"
string = reverse(string)
print("Reversed string is " + string)

```
### Linked Lists
```
# Python3 program to reverse a linked
# list using stack

# Link list node
class Node:
	
	def __init__(self, data, next):
		self.data = data
		self.next = next

class LinkedList:
	
	def __init__(self):
		self.head = None
		
	# Function to push a new Node in
	# the linked list
	def push(self, new_data):
	
		new_node = Node(new_data, self.head)
		self.head = new_node
	
	# Function to reverse linked list
	def reverseList(self):
	
		# Stack to store elements of list
		stk = []
	
		# Push the elements of list to stack
		ptr = self.head
		while ptr.next != None:
			stk.append(ptr)
			ptr = ptr.next
	
		# Pop from stack and replace
		# current nodes value'
		self.head = ptr
		while len(stk) != 0:
			ptr.next = stk.pop()
			ptr = ptr.next
		
		ptr.next = None
	
	# Function to print the Linked list
	def printList(self):
		
		curr = self.head
		while curr:
			print(curr.data, end = " ")
			curr = curr.next

# Driver Code
if __name__ == "__main__":

	# Start with the empty list
	linkedList = LinkedList()

	# Use push() to construct below list
	# 1.2.3.4.5
	linkedList.push(5)
	linkedList.push(4)
	linkedList.push(3)
	linkedList.push(2)
	linkedList.push(1)

	linkedList.reverseList()

	linkedList.printList()
```
## Check for balanced paranthesis using Stack
```
# Python3 program to check for
# balanced brackets.

# function to check if
# brackets are balanced


def areBracketsBalanced(expr):
	stack = []

	# Traversing the Expression
	for char in expr:
		if char in ["(", "{", "["]:

			# Push the element in the stack
			stack.append(char)
		else:

			# IF current character is not opening
			# bracket, then it must be closing.
			# So stack cannot be empty at this point.
			if not stack:
				return False
			current_char = stack.pop()
			if current_char == '(':
				if char != ")":
					return False
			if current_char == '{':
				if char != "}":
					return False
			if current_char == '[':
				if char != "]":
					return False

	# Check Empty Stack
	if stack:
		return False
	return True


# Driver Code
if __name__ == "__main__":
	expr = "{()}[]"

	# Function call
	if areBracketsBalanced(expr):
		print("Balanced")
	else:
		print("Not Balanced")

```

###### Note: Code referenced from GeeksforGeeks
