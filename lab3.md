## Lab Report 3

---  

**Part 1**  

Failure-inducing Input
```
@Test
public void testAverageFail() { 
    double[] input1 = {3, 3, 4, 5};
    assertEquals(4.0, ArrayExamples.averageWithoutLowest((input1)), 0.0001); //delta is for precision issues
}
```   

Non-failure-inducing Input
```
@Test
public void testAveragePass() { 
    double[] input1 = {3, 4, 5};
    assertEquals(4.0, ArrayExamples.averageWithoutLowest((input1)), 0.0001); //delta is for precision issues
}
```

Output of Running Tests
<img width="904" alt="Screen Shot 2023-11-05 at 6 49 19 PM" src="https://github.com/jmmendelson/cse15l-lab-reports/assets/130113062/54fc2ace-7528-4b47-b171-d3fed9aec653">   

Original Code   
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest){ sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

Code Fix   
```
static double averageWithoutLowest(double[] arr) {
    boolean lowestIgnored = false;
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num == lowest && lowestIgnored == false) { 
        lowestIgnored = true;
      } else {
        sum += num;
      }
    }
    return sum / (arr.length - 1);
  }
```

Explanation for Code Fix: The issue with the code before the fix was that multiple instances of the lowest value are ignored, rather than just 1. To fix this, 
I created a boolean value lowestIgnored to check if the lowest has been ignored, so the first time that the lowest is ignored when summing the numbers from the   
array, the lowest value isn't added and lowestIgnored is set to true. As the for loop continues, the rest of the numbers in the array are added up, including other   
instances of the lowestValue.

**Part 2**   

Command: grep   
Options: -i, -r, -l, -v
