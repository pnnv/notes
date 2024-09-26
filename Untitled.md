~~

**Answers to Interview Questions:**  
  
**Operating Systems:**

- **How does a system boot up and how is the OS loaded?**
    - BIOS/UEFI initializes hardware, finds the bootloader, bootloader loads the OS kernel into memory, kernel initializes core systems and starts necessary processes.
- **Difference between multicore vs multiprocessor?**
    - Multicore: Multiple cores on a single CPU chip, sharing resources like cache and memory.
    - Multiprocessor: Multiple physical CPUs, each with its own resources.
- **What is virtual memory, and why is it needed?**
    - Virtual memory is a memory management technique that allows processes to use more memory than is physically available by swapping data between RAM and disk. It's needed to run large programs and multiple programs simultaneously.
- **Demand Paging vs Pure Demand Paging and disadvantages of virtual memory.**
    - Demand Paging: Pages are loaded into RAM only when needed.
    - Pure Demand Paging: No pages are preloaded, causing potential delays.
    - Disadvantages of virtual memory: Can lead to thrashing (excessive swapping) and performance issues if not managed properly.
- **Paging in OS, page table, ASID in page table, and segmentation in OS during paging.**
    - Paging: Divides memory into fixed-size pages, allowing efficient allocation and swapping.
    - Page table: Stores mappings between virtual addresses and physical addresses.
    - ASID (Address Space Identifier): Uniquely identifies a process's address space in the page table.
    - Segmentation: Divides memory into variable-size segments based on logical divisions of a program.
- **Locks vs Semaphores, uses of counting semaphore.**
    - Locks: Provide exclusive access to a shared resource.
    - Semaphores: Allow a limited number of threads to access a resource simultaneously.
    - Counting semaphore: Used to control access to a resource with multiple instances.
- **Synchronize four threads (write, read, allocate, deallocate).**
    - Use semaphores to coordinate access to shared memory and prevent race conditions.
- **Handle busy waiting and deallocation of unallocated memory.**
    - Use condition variables to block threads until a condition is met, avoiding busy waiting. Add checks to ensure memory is allocated before reading/deallocating.

**Compiler Design:**

- **Is C++ compiled or interpreted?**
    - C++ is primarily a compiled language, although some implementations may include interpretation for specific features.
- **Explain the different phases of a compiler and their outputs.**
    - Lexical analysis: Converts source code into tokens.
    - Syntax analysis: Checks for grammatical correctness and builds a parse tree.
    - Semantic analysis: Checks for type errors and other semantic issues.
    - Intermediate code generation: Generates an intermediate representation of the code.
    - Optimization: Improves code efficiency.
    - Code generation: Generates machine code or assembly code.
- **Phases of language processing system.**
    - Compilation: Translates source code into machine code.
    - Linking: Combines object files and libraries to create an executable.
    - Loading: Loads the executable into memory for execution.

**DSA and C++:**

- **Reverse a linked list recursively and iteratively.**
    - Recursive: Recursively reverse the rest of the list and attach the current node at the end.
    - Iterative: Use three pointers to traverse the list and reverse the links.
- **Bit manipulation question (specific question not provided).**
    - Depends on the specific question, but common techniques include bitwise AND, OR, XOR, shifting, and masking.
- **Create, traverse, and deallocate a 2D character array in C++ using dynamic memory allocation.**
    - Use `new` to allocate memory for the array, nested loops to traverse it, and `delete` to deallocate memory.

**2nd Technical Interview:**

- **Designing a scalable database for an e-commerce platform.**
    - Use a combination of techniques like sharding, replication, caching, and NoSQL databases to handle large amounts of data and traffic.
- **Multithreading in Java vs C++.**
    - Java: Built-in threading support with the `Thread` class and synchronization mechanisms.
    - C++: Lower-level threading libraries (e.g., pthreads) requiring manual memory management and synchronization.
- **Software development lifecycle (SDLC).**
    - Requirement analysis, design, implementation, testing, deployment, maintenance.
- **Asynchronous JavaScript.**
    - Uses callbacks, promises, and async/await to handle non-blocking operations like network requests.

The questions mentioned in the document are:

- **Computer Networking Questions:** The interviewer started with questions on Computer Networking, but the candidate requested to change the topic as they had not prepared for it. Specific questions on Computer Networking are not mentioned.
- **Operating System (OS) Questions:**
    - Questions about Semaphores, Kernels, and Critical Sections. Specific questions on these topics are not detailed in the document.
- **Data Structures and Algorithms (DSA) Questions:**
    - **Question 1:** Find the middle node of a linked list.
        - **Approach 1 (Optimized):** Using slow and fast pointers.
        - **Approach 2 (Brute Force):** Counting the length of the list and traversing half the length.
    - **Question 2:** Search for a substring in a given string.
        - **Approach 1 (Brute Force):** Searching for all possible substrings.
        - **Approach 2 (Efficient):** Applying the KMP algorithm.
- **General Questions:**
    - Questions about the candidate's department, college, strengths, and weaknesses.
- **Managerial Round Questions:**
    - Detailed questions about the candidate's projects and work experience mentioned in their resume.
- **ETR Connect (HR) Round Questions:**
    - Questions about the candidate's willingness to relocate, plans for higher studies, and alignment of interests with the company.
    - Questions about stipend, location, and working days during the internship.

**Detailed Answers (Based on Common Interview Practices):**  
  
**Computer Networking:**

- Questions could include topics like OSI model, TCP/IP, routing protocols, subnetting, etc. Preparation in these areas would be beneficial.

**Operating System:**

- **Semaphores:** Explain their purpose for synchronization and how they work (counting vs. binary semaphores).
- **Kernels:** Discuss the role of the kernel in managing system resources and providing services to applications.
- **Critical Sections:** Explain what they are, why they are needed, and how mutual exclusion is achieved (e.g., using locks or semaphores).

**Data Structures and Algorithms:**

- **Middle Node of Linked List:**
    - **Approach 1 (Slow and Fast Pointers):** Explain how two pointers, one moving at twice the speed of the other, can be used to find the middle node efficiently.
    - **Approach 2 (Brute Force):** Explain how to traverse the list once to count the nodes and then traverse again to find the middle node.
- **Substring Search:**
    - **Approach 1 (Brute Force):** Explain how to compare the substring with all possible substrings of the given string.
    - **Approach 2 (KMP Algorithm):** Explain the concept of the KMP algorithm and how it uses a prefix table to avoid unnecessary comparisons, leading to a more efficient search.

**General/HR Questions:**

- Be prepared to answer questions about your strengths, weaknesses, career goals, and reasons for applying to the company.
- Research the company and its culture to demonstrate your interest and alignment.

**Note:** The specific questions asked in an interview can vary depending on the interviewer and the position. It's always a good idea to be well-prepared on a wide range of topics and to practice answering common interview questions.

Cisco Interview Experience Questions and Answers (Based on Rohit Kumar's Experience)  
  
**Operating Systems**

1. **What is an Operating System?**
    - An operating system (OS) is the software that manages computer hardware and software resources and provides common services for computer programs.
2. **What are the types of Operating System?**
    - Common types include:
        - Batch OS (e.g., early mainframe systems)
        - Time-sharing OS (e.g., Unix, Linux, macOS)
        - Distributed OS (e.g., network operating systems)
        - Real-time OS (e.g., used in embedded systems)
        - Multitasking OS
        - Multi-user OS
3. **What is Kernel? And what is the difference between OS and Kernel?**
    - The kernel is the core part of the operating system that handles critical tasks like memory management, process management, device management, and system calls.
    - The OS includes the kernel and other user-level components like shells, file systems, and user interfaces.
4. **What is Memory Management?**
    - Memory management is the process of allocating and deallocating memory space to processes as needed. It ensures efficient memory usage, prevents memory leaks, and handles virtual memory.

**Object-Oriented Programming (OOP)**

1. **Interviewer asked me about the pillars of OOP.**
    - The four main pillars of OOP are:
        - Inheritance: Creating new classes (subclasses) that inherit properties and behaviors from existing classes (superclasses).
        - Polymorphism: The ability of objects of different classes to respond to the same method call in different ways.
        - Abstraction: Hiding complex implementation details and showing only essential features to the user.
        - Encapsulation: Bundling data (attributes) and the methods that operate on that data into a single unit (class).
2. **How is it beneficial to use the OOP concept?**
    - OOP provides several benefits:
        - Modularity: Code is organized into classes, making it easier to manage and maintain.
        - Reusability: Inheritance and polymorphism promote code reuse.
        - Flexibility: Polymorphism allows for flexible and adaptable code.
        - Maintainability: Encapsulation helps isolate changes and reduce the impact of bugs.
3. **What are the types of Inheritance along with examples.**
    - Types of inheritance:
        - Single inheritance: A class inherits from only one superclass.
        - Multiple inheritance: A class inherits from multiple superclasses. (Not supported in all languages like Java)
        - Multilevel inheritance: A class inherits from a superclass, which itself inherits from another superclass.
        - Hierarchical inheritance: Multiple subclasses inherit from a single superclass.
        - Hybrid inheritance: A combination of multiple and multilevel inheritance.

**Computer Networks (CN)**

1. **What have I studied about CN?** (This is personal to the interviewee, but a good answer would mention layers, protocols, and basic networking concepts.)
2. **What are the different Layers of the OSI Model?**
    - The seven layers of the OSI model are:
        - Application
        - Presentation
        - Session
        - Transport
        - Network
        - Data Link
        - Physical
3. **Function of each of the Layers?**
    - Briefly:
        - Application: User interaction and application services.
        - Presentation: Data formatting, encryption, and compression.
        - Session: Establishing, managing, and terminating sessions between applications.
        - Transport: End-to-end communication, reliability, and flow control.
        - Network: Logical addressing and routing.
        - Data Link: Physical addressing (MAC addresses), error detection, and flow control.
        - Physical: Transmission of raw bits over the physical medium.
4. **I was asked about the working of the INTERNET in Layman terms in the context of Computer Network.**
    - A simple explanation could involve:
        - Devices connecting to local networks (e.g., Wi-Fi)
        - Local networks connecting to Internet Service Providers (ISPs)
        - ISPs forming a network of networks to exchange data
        - Data packets traveling through routers to reach their destination
        - Protocols like TCP/IP ensuring reliable communication

**DSA**

- Questions in this section were specific to the candidate's knowledge and experience with data structures like LinkedList, Graph, Tree, etc.

**Additional Questions**

- **What is the difference between C++ and Python? What are the scenarios in which python is preferred?**
    - Key differences:
        - C++ is a compiled language, while Python is an interpreted language.
        - C++ is generally faster for performance-critical applications, while Python is often easier to read and write


#### todo~
- [ ] **os fundamentals**
	- [x] processes / threads
	- [x] philosopher's problem
	- [x] critical section
	- [x] deadlocks and ways to handle them
	- [x] semaphores (in detail)
	- [x] multi threading
	- [ ] disc scheduling problem
- [x] time and space complexity
- [ ] servers with RAM
- [ ] microservices (definition only (?))
- [ ] swapping two numbers (different ways)
- [ ] diff b/w inf and undefined
- [x] scheduling algorithms
- [ ] **OOPS**
	- [x] diff b/e struct and class
	- [ ] abstract class and its use cases
	- [x] inheritance & its types
	- [ ] virtual functions
	- [ ] friend functions
	- [ ] static keyword
- [ ] **SQL**
	- [ ] queries
	- [ ] joins
- [ ] System Design
	- [ ] vertical and horizontal scaling
	- [ ] how to synchronise ticket booking across multiple locations
- [ ] DDos attack?
- [ ] **puzzles**
	- [ ] three jug puzzle
	- [ ] hourglass problem
	- [ ] gold bar and bags related something
- [ ] react, state management, redux (how is it different than inbuilt state management library)
- [ ] avl trees
- [ ] bst (implementation from scratch, search, insert, remove)
- [ ] reverse a string using recursion only
- [ ] internal implementations of hashmap and collisions in hashmaps
- [ ] irl examples of data structures
- [ ] **linked list**
	- [ ] remove loop from a linked list
	- [ ] nth node form the end
##### misc / random problems
- [ ] kadenes / max sum subarray
- [ ] heap sort
- [ ] remove duplicates from a sorted array in place 
- [ ] first non repeating char in a string
- [ ] segragate 0, 1, 2 without using extraspace
- [ ] sort a queue, without using extra space
- [ ] there's a stream of numbers incoming and at any point, we need to determine the median of those numbers.

896269295800188940