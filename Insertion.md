## **Question 1 **  
Write a C program to insert a node at the beginning of a singly linked list and print the list.

---

### **Code with Explanation**
```c
#include <stdio.h>
#include <stdlib.h> // Required for malloc and free functions

// Definition of a Node structure for a singly linked list
struct Node {
    int data;          // Data field to store the value
    struct Node* next; // Pointer to the next node in the list
};

// Function to insert a node at the beginning of the list
struct Node* insertAtBeginning(struct Node* head, int newData) {

    // Step 1: Allocate memory for a new node
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    // Step 2: Check if memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed\n");
        return head;  // If allocation fails, return the existing head
    }

    // Step 3: Assign the value to the new node
    newNode->data = newData;

    // Step 4: Make the new node point to the current head (old first node)
    newNode->next = head;

    // Step 5: Update the head to point to the new node
    head = newNode;

    return head; // Return the updated head of the list
}

// Function to print the linked list
void printList(struct Node* head) {
    struct Node* temp = head; // Temporary pointer to traverse the list

    printf(" Insert 120 at Beginning : ");
    
    // Traverse the list and print each node's data
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    
    printf("NULL\n"); // Indicates the end of the linked list
}

// Main function
int main() {
    // Step 1: Initialize an empty linked list
    struct Node* head = NULL;

    // Step 2: Insert elements at the beginning
    head = insertAtBeginning(head, 12);  // List: 12
    head = insertAtBeginning(head, 57);  // List: 57 -> 12
    head = insertAtBeginning(head, 48);  // List: 48 -> 57 -> 12
    head = insertAtBeginning(head, 23);  // List: 23 -> 48 -> 57 -> 12
    head = insertAtBeginning(head, 120); // List: 120 -> 23 -> 48 -> 57 -> 12

    // Step 3: Print the linked list
    printList(head);

    return 0; // Program ends successfully
}
```

---

## **Understanding Function Parameters & Logic**

### **1️⃣ `insertAtBeginning(struct Node* head, int newData)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
  - `int newData` → The integer value to be inserted.
- **Logic:**
  - A new node is created using `malloc()`.
  - The new node is assigned the given `newData`.
  - The `next` pointer of the new node is set to point to the current head.
  - The head is updated to point to this new node.
  - The updated head is returned.

---

### **2️⃣ `printList(struct Node* head)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
- **Logic:**
  - A loop traverses the linked list, printing each node's `data`.
  - The loop continues until `temp` becomes `NULL` (end of the list).
  - Finally, `NULL` is printed to indicate the end of the list.

---

### **3️⃣ `main()`**
- **Creates an empty linked list (`head = NULL`).**
- **Calls `insertAtBeginning()` multiple times to insert elements at the beginning.**
- **Prints the final linked list using `printList()`.**

---

## **Final Output**
```
 Insert 120 at Beginning : 120 -> 23 -> 48 -> 57 -> 12 -> NULL
```
Here, `120` is inserted at the beginning, followed by other inserted elements.
---

Here’s a detailed explanation of your program, focusing on function parameters and internal logic.

---

## **Question 2**  
Write a C program to insert a node at the end of a singly linked list and print the list.

---

### **Code with Explanation**
```c
#include <stdio.h>
#include <stdlib.h> // Required for malloc and free functions

// Definition of a Node structure for a singly linked list
struct Node {
    int data;          // Data field to store the value
    struct Node* next; // Pointer to the next node in the list
};

// Function to insert a node at the end of the list
struct Node* insertAtEnd(struct Node* head, int newData) {

    // Step 1: Allocate memory for a new node
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    // Step 2: Check if memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed\n");
        return head;  // If allocation fails, return the existing head
    }

    // Step 3: Assign the value to the new node
    newNode->data = newData;

    // Step 4: Since this is the last node, its next pointer must be NULL
    newNode->next = NULL;

    // Step 5: If the linked list is empty, make this new node the head
    if (head == NULL) {
        return newNode;
    }

    // Step 6: Traverse the list to find the last node
    struct Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }

    // Step 7: Attach the new node at the end
    temp->next = newNode;

    return head; // Return the updated head of the list
}

// Function to print the linked list
void printList(struct Node* head) {
    struct Node* temp = head; // Temporary pointer to traverse the list

    printf(" Insert 120 at END : ");
    
    // Traverse the list and print each node's data
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    
    printf("NULL\n"); // Indicates the end of the linked list
}

// Main function
int main() {
    // Step 1: Initialize an empty linked list
    struct Node* head = NULL;

    // Step 2: Insert elements at the end
    head = insertAtEnd(head, 23);  // List: 23
    head = insertAtEnd(head, 48);  // List: 23 -> 48
    head = insertAtEnd(head, 57);  // List: 23 -> 48 -> 57
    head = insertAtEnd(head, 4);   // List: 23 -> 48 -> 57 -> 4
    head = insertAtEnd(head, 12);  // List: 23 -> 48 -> 57 -> 4 -> 12

    // Step 3: Insert 120 at the end
    head = insertAtEnd(head, 120); // List: 23 -> 48 -> 57 -> 4 -> 12 -> 120

    // Step 4: Print the linked list
    printList(head);

    return 0; // Program ends successfully
}
```

---

## **Understanding Function Parameters & Logic**

### **1️⃣ `insertAtEnd(struct Node* head, int newData)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
  - `int newData` → The integer value to be inserted.
- **Logic:**
  - A new node is created using `malloc()`.
  - The new node is assigned the given `newData`.
  - If the list is empty (`head == NULL`), the new node becomes the head.
  - Otherwise, the function traverses to the last node.
  - The new node is attached to the last node.

---

### **2️⃣ `printList(struct Node* head)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
- **Logic:**
  - A loop traverses the linked list, printing each node's `data`.
  - The loop continues until `temp` becomes `NULL` (end of the list).
  - Finally, `NULL` is printed to indicate the end of the list.

---

### **3️⃣ `main()`**
- **Creates an empty linked list (`head = NULL`).**
- **Calls `insertAtEnd()` multiple times to insert elements at the end.**
- **Prints the final linked list using `printList()`.**

---

## **Final Output**
```
 Insert 120 at END : 23 -> 48 -> 57 -> 4 -> 12 -> 120 -> NULL
```
Here, `120` is inserted at the end, following the other inserted elements.
---

# **Question 3:**  
Write a C program to insert a node **after a given key** in a singly linked list and print the updated list.

---

## **Code with Explanation**
```c
#include <stdio.h>
#include <stdlib.h> // Required for malloc and free functions

// Definition of a Node structure for a singly linked list
struct Node {
    int data;          // Data field to store the value
    struct Node* next; // Pointer to the next node in the list
};

// Function to insert a node after a specific key
struct Node* insertAfter(struct Node* head, int key, int newData) {
    struct Node* temp = head; // Temporary pointer to traverse the list

    // Step 1: Traverse the list to find the node with the given key
    while (temp != NULL && temp->data != key) {
        temp = temp->next;
    }

    // Step 2: If the key is not found, print a message and return the original list
    if (temp == NULL) {
        printf("Node with value %d not found.\n", key);
        return head;
    }

    // Step 3: Allocate memory for the new node
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        printf("Memory allocation failed\n");
        return head; // If allocation fails, return the existing head
    }

    // Step 4: Assign the value to the new node
    newNode->data = newData;

    // Step 5: Insert the new node after the found node
    newNode->next = temp->next; 
    temp->next = newNode;  

    return head; // Return the updated head of the list
}

// Function to insert a node at the end of the list
struct Node* insertAtEnd(struct Node* head, int newData) {
    // Step 1: Allocate memory for a new node
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    // Step 2: Check if memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed\n");
        return head;
    }

    // Step 3: Assign the value to the new node
    newNode->data = newData;
    newNode->next = NULL;

    // Step 4: If the linked list is empty, make this new node the head
    if (head == NULL) {
        return newNode;
    }

    // Step 5: Traverse the list to find the last node
    struct Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }

    // Step 6: Attach the new node at the end
    temp->next = newNode;

    return head; // Return the updated head of the list
}

// Function to print the linked list
void printList(struct Node* head) {
    struct Node* temp = head; // Temporary pointer to traverse the list

    printf("SLL Inserting 120 after 48: ");
    
    // Traverse the list and print each node's data
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    
    printf("NULL\n"); // Indicates the end of the linked list
}

// Main function
int main() {
    // Step 1: Initialize an empty linked list
    struct Node* head = NULL;

    // Step 2: Insert elements at the end
    head = insertAtEnd(head, 23);  // List: 23
    head = insertAtEnd(head, 48);  // List: 23 -> 48
    head = insertAtEnd(head, 57);  // List: 23 -> 48 -> 57
    head = insertAtEnd(head, 4);   // List: 23 -> 48 -> 57 -> 4
    head = insertAtEnd(head, 12);  // List: 23 -> 48 -> 57 -> 4 -> 12

    // Step 3: Insert 120 after 48
    head = insertAfter(head, 48, 120); // List: 23 -> 48 -> 120 -> 57 -> 4 -> 12

    // Step 4: Print the linked list
    printList(head);

    return 0; // Program ends successfully
}
```

---

## **Understanding Function Parameters & Logic**

### **1️⃣ `insertAfter(struct Node* head, int key, int newData)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
  - `int key` → The value **after which** the new node will be inserted.
  - `int newData` → The integer value of the new node.
- **Logic:**
  - The function first searches for `key` in the list.
  - If found, it creates a new node with `newData` and inserts it **after** the key.
  - If the key is not found, a message is printed.

---

### **2️⃣ `insertAtEnd(struct Node* head, int newData)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
  - `int newData` → The integer value of the new node.
- **Logic:**
  - A new node is created using `malloc()`.
  - The new node is assigned the given `newData`.
  - If the list is empty (`head == NULL`), the new node becomes the head.
  - Otherwise, the function traverses to the last node.
  - The new node is attached to the last node.

---

### **3️⃣ `printList(struct Node* head)`**
- **Parameters:**
  - `struct Node* head` → Pointer to the first node of the linked list.
- **Logic:**
  - A loop traverses the linked list, printing each node's `data`.
  - The loop continues until `temp` becomes `NULL` (end of the list).
  - Finally, `NULL` is printed to indicate the end of the list.

---

### **4️⃣ `main()`**
- **Creates an empty linked list (`head = NULL`).**
- **Calls `insertAtEnd()` multiple times to insert elements at the end.**
- **Calls `insertAfter()` to insert `120` after `48`.**
- **Prints the final linked list using `printList()`.**

---

## **Final Output**
```
SLL Inserting 120 after 48: 23 -> 48 -> 120 -> 57 -> 4 -> 12 -> NULL
```
Here, `120` is inserted **after** `48`, following the other inserted elements.
---


### **📌 Question 4:**
Write a C program to perform the following operations on a **Doubly Linked List**:
1. Insert a node at the **beginning** of the list.
2. Print the linked list.

Given a linked list:  
`23 -> 48 -> 57 -> 4 -> 12`,  
Insert `120` **at the beginning** and print the updated list.

---

### **📜 C Program**
```c
#include <stdio.h>
#include <stdlib.h>
#include <stdint.h> // Include stdint.h for uint16_t

// Define a structure for a node in the doubly linked list
struct Node {
    uint16_t data;         // Using uint16_t instead of int to store 16-bit unsigned integer
    struct Node* next;     // Pointer to the next node
    struct Node* prev;     // Pointer to the previous node
};

// Function to insert a new node at the beginning of the doubly linked list
void insertAtBeginning(struct Node** head, uint16_t value) {
    // Step 1: Create a new node
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    // Step 2: Assign the data and initialize pointers
    newNode->data = value; // Store the given value
    newNode->prev = NULL;  // The previous pointer of the new node is NULL (since it's the first node)

    // Step 3: If the list is empty, set next to NULL
    if (*head == NULL) {
        newNode->next = NULL; 
    } else {
        // Step 4: Otherwise, link new node to the current head
        newNode->next = *head;    // New node points to the old head
        (*head)->prev = newNode;  // Old head's previous pointer now points to new node
    }

    // Step 5: Update head to point to the new node
    *head = newNode;
}

// Function to print the doubly linked list
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%u -> ", temp->data); // %u is used to print uint16_t values
        temp = temp->next;  // Move to the next node
    }
    printf("NULL\n"); // Indicate the end of the list
}

int main() {
    struct Node* head = NULL; // Initialize an empty doubly linked list

    // Insert elements into the doubly linked list
    insertAtBeginning(&head, 12);
    insertAtBeginning(&head, 4);
    insertAtBeginning(&head, 57);
    insertAtBeginning(&head, 48);
    insertAtBeginning(&head, 23);

    // Insert 120 at the beginning
    insertAtBeginning(&head, 120);

    // Print the updated list
    printf("Inserting 120 at the beginning: ");
    printList(head);

    return 0;
}
```

---

### **📝 Explanation of Each Step**
#### **📌 1. `#include <stdint.h>`**
- The `stdint.h` library is included to use **`uint16_t`**, which ensures we use a **16-bit unsigned integer** instead of a regular `int`.  
- `uint16_t` stores numbers from `0` to `65535`, reducing unnecessary memory usage for small numbers.

#### **📌 2. Struct Definition (`struct Node`)**
```c
struct Node {
    uint16_t data;         // Stores the integer value (16-bit unsigned)
    struct Node* next;     // Pointer to the next node in the list
    struct Node* prev;     // Pointer to the previous node in the list
};
```
- **`data`**: Stores the value of the node.
- **`next`**: Points to the next node in the list.
- **`prev`**: Points to the previous node (since it's a **Doubly Linked List**).

---

#### **📌 3. `insertAtBeginning` Function**
```c
void insertAtBeginning(struct Node** head, uint16_t value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node)); // Allocate memory for new node
    newNode->data = value;  // Assign value
    newNode->prev = NULL;   // Since it’s the first node, prev is NULL

    if (*head == NULL) {
        newNode->next = NULL;  // If list is empty, next is also NULL
    } else {
        newNode->next = *head; // New node points to the old head
        (*head)->prev = newNode; // Old head’s prev now points to new node
    }

    *head = newNode;  // Update head pointer to the new node
}
```
- **Handles both cases**: If the list is empty or contains nodes.
- **Maintains bidirectional links** (prev & next) for the doubly linked list.

---

#### **📌 4. `printList` Function**
```c
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%u -> ", temp->data); // Print node data
        temp = temp->next;  // Move to the next node
    }
    printf("NULL\n"); // End of the list
}
```
- **Traverses** the list from **head to tail**.
- **Prints** each node's value in **"value -> value -> NULL"** format.

---

#### **📌 5. `main` Function**
```c
int main() {
    struct Node* head = NULL; // Initialize an empty linked list

    // Insert elements into the doubly linked list
    insertAtBeginning(&head, 12);
    insertAtBeginning(&head, 4);
    insertAtBeginning(&head, 57);
    insertAtBeginning(&head, 48);
    insertAtBeginning(&head, 23);

    // Insert 120 at the beginning
    insertAtBeginning(&head, 120);

    // Print the updated list
    printf("Inserting 120 at the beginning: ");
    printList(head);

    return 0;
}
```
- **Creates** an empty list (`head = NULL`).
- **Inserts** `12, 4, 57, 48, 23` **at the beginning**.
- **Finally inserts `120` at the beginning** and prints the updated list.

---

### **📌 Expected Output**
```
Inserting 120 at the beginning: 120 -> 23 -> 48 -> 57 -> 4 -> 12 -> NULL
```
✅ **`120` is successfully inserted at the beginning!** 🚀

---

### **✅ Advantages of Using `uint16_t`**
1. **Memory Efficient** 🏆  
   - `uint16_t` **(16-bit)** is smaller than `int` (which is typically 32-bit or 64-bit).  
   - Saves memory if we store **small numbers**.

2. **Fixed Size** 📏  
   - Always **16-bit** across **all platforms** (portable).

3. **Prevents Negative Values** 🚫  
   - Since it's **unsigned**, it **never stores negative values**.

---

### **💡 Key Takeaways**
✔ We implemented **Doubly Linked List** insertion at the **beginning**.  
✔ Used **`uint16_t`** for efficient memory usage.  
✔ Included **comments & explanations** for each step.  
✔ Output verified with correct **linked list structure**.

---
## **Question 5**

#include <stdio.h>
#include <stdlib.h>
#include <stdint.h> // Include stdint.h for uint16_t

// Define a structure for a node in the doubly linked list
struct Node {
    uint16_t data;         // Using uint16_t instead of int to store 16-bit unsigned integer
    struct Node* next;     // Pointer to the next node
    struct Node* prev;     // Pointer to the previous node
};

// Function to insert a new node at the end of the doubly linked list
void insertAtEnd(struct Node** head, uint16_t value) {
    // Step 1: Create a new node
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL; // The new node will be the last node, so next is NULL

    // Step 2: If the list is empty, make new node the head
    if (*head == NULL) {
        newNode->prev = NULL; // Since it's the first node, prev is NULL
        *head = newNode;
        return;
    }
    
    // Step 3: Traverse to the last node
    struct Node* temp = *head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    
    // Step 4: Link the new node at the end
    temp->next = newNode;
    newNode->prev = temp;
}

// Function to print the doubly linked list
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%u -> ", temp->data); // %u for uint16_t values
        temp = temp->next;
    }
    printf("NULL\n"); // Indicate end of the list
}

int main() {
    struct Node* head = NULL; // Initialize an empty doubly linked list

    // Insert elements into the doubly linked list
    insertAtEnd(&head, 23);
    insertAtEnd(&head, 48);
    insertAtEnd(&head, 57);
    insertAtEnd(&head, 4);
    insertAtEnd(&head, 12);

    // Insert 120 at the end
    insertAtEnd(&head, 120);
    
    // Print the updated list
    printf("Inserting 120 at the END: ");
    printList(head);

    return 0;
}
---

Let's break down the function parameters and logic inside the `insertAtEnd` function carefully so you understand it well. 🚀  

---

### **Function Definition**  
```c
void insertAtEnd(struct Node** head, uint16_t value)
```
#### **Understanding Parameters**
1. **`struct Node** head`**:  
   - This is a **pointer to a pointer** of type `struct Node`.  
   - The reason we use `struct Node**` instead of `struct Node*` is that we want to modify the original head of the linked list if it's empty.  
   - If we used `struct Node* head`, the changes would only apply inside the function and wouldn't affect the original linked list.
2. **`uint16_t value`**:  
   - This is the value that we want to insert at the end of the linked list.  
   - We use `uint16_t` (16-bit unsigned integer) to ensure the data type is suitable for small positive numbers.

---

### **Inside the Function**
```c
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
newNode->data = value;
newNode->next = NULL;
```
#### **What’s happening here?**
- We **create a new node** using `malloc`, which allocates memory dynamically.  
- `newNode->data = value;` → We store the given `value` inside the new node.  
- `newNode->next = NULL;` → Since this will be the last node, its `next` pointer is set to `NULL`.

---

### **Checking If the List Is Empty**
```c
if (*head == NULL) {
    newNode->prev = NULL; 
    *head = newNode; 
    return;
}
```
#### **Logic:**
- If `*head == NULL`, it means the list is empty.
- `newNode->prev = NULL;` → Since this is the first node, its `prev` pointer is also `NULL`.
- `*head = newNode;` → The new node becomes the head of the list.
- `return;` → Exit the function since we’ve inserted the node.

---

### **Traversing to the Last Node**
```c
struct Node* temp = *head;
while (temp->next != NULL) {
    temp = temp->next;
}
```
#### **Logic:**
- We start at the head (`temp = *head`).
- We move forward (`temp = temp->next`) until `temp->next == NULL`, meaning we have reached the last node.

---

### **Linking the New Node at the End**
```c
temp->next = newNode;
newNode->prev = temp;
```
#### **Logic:**
- `temp->next = newNode;` → The last node’s `next` pointer is updated to point to the new node.
- `newNode->prev = temp;` → The new node’s `prev` pointer is set to point back to the previous last node.

---

### **Final Output**
Once we insert all elements and print the list, the output will be:  
```
Inserting 120 at the END: 23 -> 48 -> 57 -> 4 -> 12 -> 120 -> NULL
```
This confirms the node was correctly added at the end!

---
#### **Key Takeaways:**
1️⃣ **Pointer to a pointer (`struct Node** head`)** is used so we can modify the original list.  
2️⃣ **`malloc(sizeof(struct Node))`** dynamically allocates memory for the new node.  
3️⃣ **Traversing the list** is required to reach the last node before insertion.  
4️⃣ **Updating `next` and `prev` pointers** ensures proper linking in the doubly linked list.
---
### **Doubly Linked List: Inserting a Node at the End** 🚀

#### **Overview**
In a **doubly linked list**, each node contains three elements:
- **Data**: Stores the actual value.
- **Next pointer**: Points to the next node in the list.
- **Prev pointer**: Points to the previous node in the list.

Inserting a node at the end of a doubly linked list requires careful management of pointers, especially when the list is empty or contains multiple nodes.

---

### **Function Definition**
```c
void insertAtEnd(struct Node** head, uint16_t value)
```

#### **Function Parameters**
1. **`struct Node** head`**: 
   - A pointer to a pointer to the head of the linked list. This allows modifying the head of the list if the list is initially empty.
   
2. **`uint16_t value`**: 
   - The value to be inserted at the end of the list. The type `uint16_t` ensures the value is a 16-bit unsigned integer.

---

### **Steps in the `insertAtEnd` Function** 📚

#### 1. **Create a New Node**
```c
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
newNode->data = value;
newNode->next = NULL;
```
- **Memory Allocation**: `malloc` dynamically allocates memory for the new node.
- **Set Data**: The `data` field of the node is set to the `value` passed to the function.
- **Next Pointer**: Since the new node will be the last node, its `next` pointer is set to `NULL`.

---

#### 2. **Check if the List is Empty**
```c
if (*head == NULL) {
    newNode->prev = NULL; 
    *head = newNode; 
    return;
}
```
- **If Empty**: If `*head == NULL`, the list is empty.
  - Set the `prev` pointer of the new node to `NULL` because it’s the first node.
  - Make the new node the head of the list.
  - Exit the function after inserting the node.

---

#### 3. **Traverse to the Last Node**
```c
struct Node* temp = *head;
while (temp->next != NULL) {
    temp = temp->next;
}
```
- **Traverse the List**: Start from the head and move through the nodes until reaching the last node (i.e., where `temp->next == NULL`).

---

#### 4. **Link the New Node at the End**
```c
temp->next = newNode;
newNode->prev = temp;
```
- **Update `next` Pointer**: Set the `next` pointer of the current last node to point to the new node.
- **Update `prev` Pointer**: Set the `prev` pointer of the new node to point back to the current last node.

---

### **Final Output**
After inserting the value `120` at the end, the list will look like:
```
23 -> 48 -> 57 -> 4 -> 12 -> 120 -> NULL
```

---

### **Key Concepts and Takeaways**
1. **Pointer to a Pointer**: Using `struct Node** head` allows modifying the original head of the linked list if it’s empty.
2. **Dynamic Memory Allocation**: `malloc(sizeof(struct Node))` allocates memory for a new node.
3. **Traversal**: To insert at the end, we first need to traverse to the last node in the list.
4. **Proper Linking**: After finding the last node, we update the `next` and `prev` pointers to maintain the doubly linked structure.

---

### **Visual Representation**

1. **Initial List**: 
   ```
   NULL
   ```

2. **After Inserting `23`**:
   ```
   23 -> NULL
   ```

3. **After Inserting `48`**:
   ```
   23 <-> 48 -> NULL
   ```

4. **After Inserting `57`**:
   ```
   23 <-> 48 <-> 57 -> NULL
   ```

5. **Final List after Inserting `120`**:
   ```
   23 <-> 48 <-> 57 <-> 4 <-> 12 <-> 120 -> NULL
   ```

---

### **Summary of Key Points**
- **Insert at End**: Ensure the new node’s `next` is `NULL` and update the last node’s `next` pointer to the new node.
- **Handle Empty List**: When the list is empty, make the new node the head of the list.
- **Doubly Linked Structure**: Always maintain the `prev` pointer to ensure proper bidirectional navigation.

This approach ensures efficient insertion while maintaining the integrity of the doubly linked list.


---

### **Question 6:**  
Write a program in **C** to insert a node **at the end of a doubly linked list** and to **insert a node after a specific value** using **`uint16_t`** for integer values.

---

### **Updated Code with uint16_t and Full Explanation**
```c
#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>  // Include for uint16_t

// Define a structure for a doubly linked list node
struct Node {
    uint16_t data;        // Using uint16_t for 16-bit unsigned integer
    struct Node* next;    // Pointer to the next node
    struct Node* prev;    // Pointer to the previous node
};

// Function to insert a node at the END of the doubly linked list
void insertAtEnd(struct Node** head, uint16_t value) {
    // Step 1: Create a new node dynamically
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;  // Store the given value
    newNode->next = NULL;   // Since it's the last node, next is NULL

    // Step 2: Check if the list is empty
    if (*head == NULL) {
        newNode->prev = NULL;  // The first node has no previous node
        *head = newNode;       // Make newNode the head of the list
        return;
    }

    // Step 3: Traverse the list to reach the last node
    struct Node* temp = *head;
    while (temp->next != NULL) {
        temp = temp->next;
    }

    // Step 4: Link the new node to the last node
    temp->next = newNode;  // Last node’s next points to the new node
    newNode->prev = temp;  // New node’s prev points to the last node
}

// Function to insert a node AFTER a specific value in the doubly linked list
void insertAfterValue(struct Node** head, uint16_t afterValue, uint16_t newValue) {
    struct Node* temp = *head;  // Start from the head node

    // Step 1: Traverse the list to find the node with afterValue
    while (temp != NULL && temp->data != afterValue) {
        temp = temp->next;
    }

    // Step 2: Check if the value was found in the list
    if (temp != NULL) {
        // Step 3: Create a new node dynamically
        struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
        newNode->data = newValue;

        // Step 4: Adjust pointers to insert the node
        newNode->next = temp->next;  // New node points to the next node
        newNode->prev = temp;        // New node's prev points to temp

        // Step 5: If temp->next is not NULL, update the next node’s prev pointer
        if (temp->next != NULL) {
            temp->next->prev = newNode;
        }
        temp->next = newNode;  // Insert new node after temp
    }
}

// Function to print the linked list
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

// Main function to test the insertion operations
int main() {
    struct Node* head = NULL;  // Initialize an empty list

    // Insert elements at the END
    insertAtEnd(&head, 23);
    insertAtEnd(&head, 48);
    insertAtEnd(&head, 57);
    insertAtEnd(&head, 4);
    insertAtEnd(&head, 12);

    // Insert 120 AFTER 48
    insertAfterValue(&head, 48, 120);

    // Print the updated list
    printf("Inserting 120 after 48: ");
    printList(head);

    return 0;
}
```

---

## **Understanding Function Parameters and Inside Function Logic**  

### **1️⃣ `insertAtEnd(struct Node** head, uint16_t value)`**
#### **Function Parameters**  
- `struct Node** head`:  
  - **Pointer to a pointer** → This allows modification of the original linked list.  
  - If the list is empty, `*head = newNode;` will set the new node as the head.
- `uint16_t value`:  
  - **New value to insert at the end.**  
  - `uint16_t` is a **16-bit unsigned integer** (range: 0 to 65535), ensuring safe memory usage.

#### **Function Logic (Step-by-Step)**
1. **Create a new node**  
   - Allocate memory using `malloc()`.
   - Store `value` inside `newNode`.
   - Set `newNode->next = NULL;` (since it will be the last node).
   
2. **Check if the list is empty**  
   - If `*head == NULL`, make `newNode` the head and return.

3. **Traverse the list to find the last node**  
   - Move forward using `temp = temp->next;` until `temp->next == NULL`.

4. **Link the new node to the last node**  
   - `temp->next = newNode;` → Attach the new node at the end.  
   - `newNode->prev = temp;` → Maintain the previous link.

---

### **2️⃣ `insertAfterValue(struct Node** head, uint16_t afterValue, uint16_t newValue)`**
#### **Function Parameters**  
- `struct Node** head`: Pointer to the first node.
- `uint16_t afterValue`: The value **after** which we insert the new node.
- `uint16_t newValue`: The value of the new node.

#### **Function Logic (Step-by-Step)**
1. **Traverse the list to find `afterValue`**  
   - If found, proceed to the next step.  
   - If not found, do nothing (node isn’t inserted).

2. **Create a new node dynamically**  
   - Store `newValue` inside the new node.

3. **Adjust the pointers to insert the node correctly**  
   - `newNode->next = temp->next;` → Connect new node to the next node.
   - `newNode->prev = temp;` → Link new node to `temp`.
   - If `temp->next` exists, update its `prev` pointer.

4. **Insert new node after `temp`**  
   - `temp->next = newNode;`

---

## **🔹 Sample Output**
```
Inserting 120 after 48: 23 -> 48 -> 120 -> 57 -> 4 -> 12 -> NULL
```
✅ The value **120** is successfully inserted **after** 48.  
✅ The doubly linked list maintains its structure.

---

## **🛠 Key Takeaways**
### 🔹 **Why Use `uint16_t`?**
- It saves memory compared to `int` (which is usually 32-bit or 64-bit).
- Suitable for storing **small positive numbers** in an optimized way.

### 🔹 **Why `struct Node** head` Instead of `struct Node* head`?**
- We use `**head` because we modify the **original list**.
- If we used `*head`, modifications would **only affect the function scope**.

### 🔹 **Why Use `malloc()`?**
- `malloc(sizeof(struct Node))` dynamically allocates memory.
- This allows us to create nodes **at runtime** instead of static allocation.

---

