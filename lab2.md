# Lab Report 2

**Part 1**
Here is the code, I edited the StringSearch given already

<img width="681" alt="Screen Shot 2023-10-22 at 9 38 49 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/c568dd94-cae3-4c35-9361-d92da341250f">  

Questions:
Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

Here is the first use.  
<img width="397" alt="Screen Shot 2023-10-22 at 9 41 55 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/728b309e-0a8d-4f8b-8da5-d5570b643502">
- The main method and handleRequest method are called.
- The main method takes the port number as an argument, and an int called port is initialized with this value. handleRequest takes a URI called url (http://localhost:4000/add-message?s=Hello) as an argument, and a List of strings called lines is initialized to be empty. A string called query is initialized with the query part of url (part after "?" which is "Hello"). Lastly, an integer called count is initialized to 0.   
- The changes that occur are "1. Hello" is added to lines and count is incremented to 1.  

Here is the second use.  
<img width="496" alt="Screen Shot 2023-10-22 at 9 42 14 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/d3ec81bf-aeba-46bf-a4f8-dd128f1e0205">
- The main method and handleRequest method are called again
- The main method uses the same port number as an argument, and handleRequest takes the URI url (http://localhost:4000/add-message?s=How%20are%20you) as an argument. query is initialized with the query part of url (How%20are%20you) where %20 is a space
- The changes that occur are "2. How are you" is added to lines and count is incremented to 2. Lines now contains "1. Hello" for the first string and "2. How are you" for the second string  

**Part 2**  
Path to private key:   
<img width="476" alt="Screen Shot 2023-10-25 at 5 22 08 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/a8c48e04-b36e-415b-8a36-542072e8e6cf">  
Path to public key:  
<img width="675" alt="Screen Shot 2023-11-05 at 8 17 03 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/8a549da2-ccac-435c-8236-7e4b9ecc597b">  
Logging into ssh without password:  
<img width="758" alt="Screen Shot 2023-10-25 at 5 17 29 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/b59c8ad0-7eed-4a09-b4f0-b45cd7e7e501">  

**Part 3**  
Something I learned in week 2 that I didn't know before was that you can start a server from the IDE, I had thought that a third-party program would be needed for something like this. Something I learned in week 3 that I didn't know before was that I can make it so I can log into my account using ssh without a password. I also learned that I can use the url to control a program and be able to use values from the url.
