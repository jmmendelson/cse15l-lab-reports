# Lab Report 5  

**Part 1**  

1.) Hi everyone,
I've been working on a simple Java program that's supposed to double a number. I'm using a bash script to compile and run it.
However, the output isn't what I expected. I thought the number would be doubled, but it remains the same. Here's a screenshot of the output after running my bash script followed by my Java code:   
<img width="458" alt="Screenshot 2023-12-04 at 7 55 11 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/a102f78b-6683-4c29-bc06-bf7c10b148a4">   
<img width="470" alt="Screenshot 2023-12-04 at 7 56 05 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/c67397f9-7022-4ea5-84b3-9a30a8796c95">   
   
I think the bug might be in how I'm handling the number in my Java method. Maybe it's not updating the variable correctly? Any help would be appreciated!     

2.) Hi there,
Thank you for sharing your Java code. I see how you've implemented the `doubleNumber` method. Could you think about how Java handles variables when they are passed to methods?
Specifically, consider what happens to the variable `num` when it's passed to `doubleNumber`. Does the method modify the original `num` variable, or is something else happening?
Reflecting on this might help you identify the root cause of the issue.   
Best,   
TA  

3.) Thank you for the response,
After doing a little research I found that Java uses pass-by-value, so `doubleNumber` was working with a copy of `num`. I changed the method to return the doubled value and updated `num` 
in the main method with this returned value, and it works now.  
Thanks again!  

4.) The file & directory structure needed: You must have both the Java file and Bash script file in the same directory.   
The contents of each file before fixing the bug: The contents of `Main.java` were attached above in step 3, here are the contents of `run.sh`   
<img width="450" alt="Screenshot 2023-12-04 at 7 57 37 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/ff2b1af6-2abf-416e-b15c-3d7f7048f857">   
The full command line (or lines) you ran to trigger the bug: this was attached above in step 1   
A description of what to edit to fix the bug: The edits I made to fix the bug was changing `doubleNumber` from being void to returning an integer, and printing `doubleNumber(num)` in the 
second print statement instead of `num`   
<img width="476" alt="Screenshot 2023-12-04 at 8 03 47 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/fcf0ab3b-bcdb-4af4-9b20-6c9cbdfc97f4">   
Here is the correct output from running `run.sh`   
<img width="455" alt="Screenshot 2023-12-04 at 8 04 11 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/31f9d3d2-83f4-4f23-bcff-972cfc041e22">

**Part 2**  

Something cool I learned in the second half of the quarter is that you can edit code via the command-line. Although vim can be a bit annoying at times, 
its really handy when I'm in signed in remotely and don't have access to the IDE. I just tend to forget some of the commands in vim.
