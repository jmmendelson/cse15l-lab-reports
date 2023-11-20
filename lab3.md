# Lab Report 3

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

Explanation for Code Fix: The issue with the code before the fix was that multiple instances of the lowest value are ignored, rather than just 1. To fix this, I created a boolean value lowestIgnored to check if the lowest has been ignored, so the first time that the lowest is ignored when summing the numbers from the array, the lowest value isn't added and lowestIgnored is set to true. As the for loop continues, the rest of the numbers in the array are added up, including other instances of the lowestValue.

**Part 2**   

Command: grep   
Options: -i, -r, -l, -c

-i: Example 1  
```
maxmendelson@Maxs-MBP docsearch % grep -i 'meta-analysis' ./technical/plos/*.txt
./technical/plos/journal.pbio.0020354.txt:        for sister species pairs to know how common paraphyly is, although a recent meta-analysis
./technical/plos/journal.pbio.0020406.txt:        2004). Nonetheless, not all groups show these trends, and a recent meta-analysis, albeit
./technical/plos/pmed.0010021.txt:          than those with mild disease, but a meta-analysis based on liver size or spleen size made
./technical/plos/pmed.0010021.txt:        attractive concept, but is it correct? Another meta-analysis indicates that it is not.
./technical/plos/pmed.0020210.txt:        in the tropical world [2], and a recent meta-analysis showed that the disease is
./technical/plos/pmed.0020212.txt:        Lewis et al. meta-analysis [12] included most of the studies in Figure 2 and found that one
./technical/plos/pmed.0020212.txt:        Lewis et al. meta-analysis implicate more than 3,000 genes (18% of all known genes). For
./technical/plos/pmed.0020238.txt:        by doing a systematic review and meta-analysis of analgesic therapy for PHN, which has
```

-i: Example 2  
```
maxmendelson@Maxs-MBP docsearch % grep -i 'immunoperoxidase' ./technical/biomed/*.txt
./technical/biomed/1471-2202-4-3.txt:        immunoperoxidase technique, and to compare our findings
./technical/biomed/1471-5945-3-3.txt:          until processed. Indirect immunoperoxidase staining was
./technical/biomed/1471-5945-3-3.txt:          Immunoperoxidase Staining
./technical/biomed/1477-7827-1-13.txt:          30 min, and stored at 4°C until immunoperoxidase staining
./technical/biomed/1477-7827-1-36.txt:          immunoperoxidase immunohistochemistry [ 15 ] . For ERβ,
./technical/biomed/1477-7827-1-36.txt:          (background) and within ERα and ERβ immunoperoxidase
./technical/biomed/1477-7827-1-46.txt:          stored at -80°C until immunoperoxidase staining was
./technical/biomed/ar130.txt:          immunoperoxidase method described above. The specimens
./technical/biomed/ar407.txt:          Indirect immunoperoxidase staining was performed at 37°C
./technical/biomed/ar408.txt:          immunoperoxidase method (Vectastain ABC Elite Kit; Vector
./technical/biomed/bcr273.txt:          performed using an indirect immunoperoxidase detection
./technical/biomed/bcr273.txt:          indirect immunoperoxidase detection protocol (Vectastain
./technical/biomed/bcr303.txt:          avidin-biotin complex immunoperoxidase method as
```

What it's doing: makes the search case-insensitive. This means that it will match lines regardless of whether the characters in the search term are lowercase or uppercase.  
Why it's useful: helpful when you're not sure of the case of the text you're searching for or when the case is inconsistent.  

-r: Example 1   
```
maxmendelson@Maxs-MBP docsearch % grep -r 'subclinical' ./technical/biomed/
./technical/biomed//1471-2466-3-1.txt:        clinical or subclinical pulmonary inflammation due to
./technical/biomed//1471-2458-3-2.txt:          for subclinical disease by testing stool for 
./technical/biomed//1471-2458-2-6.txt:          liver disease. However, transient subclinical
./technical/biomed//1471-2350-3-1.txt:        subclinical (radiographic) stroke or be discordant only
./technical/biomed//cc1044.txt:        subclinical cerebral damage, increased adenylate cyclase in
./technical/biomed//1472-6882-1-10.txt:          subclinical infections these dogs might have due to their
./technical/biomed//1468-6708-3-7.txt:        presentation of heart failure in those with subclinical
./technical/biomed//1468-6708-3-7.txt:        subclinical ventricular dysfunction, but may possibly
./technical/biomed//cvm-2-6-286.txt:        subclinical infarctions that occur during otherwise
./technical/biomed//1468-6708-3-1.txt:        whom risk factors, subclinical disease, and morbidity are
./technical/biomed//ar328.txt:        inflammatory serum subclinical abnormalities. The
```

-r: Example 2   
```
maxmendelson@Maxs-MBP docsearch % grep -r 'murder' ./technical/911report/ 
./technical/911report//chapter-3.txt:                tracking down Mir Amal Kansi, the Pakistani gunman who had murdered two CIA
./technical/911report//chapter-2.txt:                declared war against God and his messenger, they called for the murder of any
./technical/911report//chapter-2.txt:                even unprovoked mass murder as righteous defense of an embattled faith. Many
./technical/911report//chapter-2.txt:                as unbelievers," because of their readiness to demonize and murder those with whom
./technical/911report//chapter-2.txt:                like most other human beings, are repelled by mass murder and barbarism whatever
./technical/911report//chapter-2.txt:                Jersey City, he distributed messages calling for the murder of unbelievers.
./technical/911report//chapter-7.txt:                suspect criminal behavior, let alone a terrorist plot to commit mass murder.
```

What it's doing: enables recursive searching. This means grep will search through all directories and subdirectories starting from the given directory and match the specified pattern in all files.  
Why it's useful: helpful when working with projects with a complex directory structure. It allows you to quickly search through all files in all directories for a specific term, saving time and effort compared to manually searching each directory.  

-l: Example 1  
```
maxmendelson@Maxs-MBP docsearch % grep -l 'WTC' ./technical/911report/*.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-9.txt
```

-l: Example 2  
```
maxmendelson@Maxs-MBP docsearch % grep -l 'phosphorylation' ./technical/plos/*.txt
./technical/plos/journal.pbio.0020311.txt
./technical/plos/journal.pbio.0020348.txt
./technical/plos/journal.pbio.0020400.txt
./technical/plos/journal.pbio.0020401.txt
./technical/plos/journal.pbio.0030076.txt
./technical/plos/journal.pbio.0030094.txt
./technical/plos/pmed.0020018.txt
./technical/plos/pmed.0020045.txt
./technical/plos/pmed.0020073.txt
./technical/plos/pmed.0020075.txt
```

What it's doing: only output the names of the files with matching lines, rather than the lines themselves. Each file name is listed only once.  
Why it's useful: This is great for when you need to know which files contain a given pattern, but you don't need the actual content of the lines.  

-c: Example 1  
```
maxmendelson@Maxs-MBP docsearch % grep -c 'terrorism' ./technical/911report/*.txt
./technical/911report/chapter-1.txt:1
./technical/911report/chapter-10.txt:14
./technical/911report/chapter-11.txt:37
./technical/911report/chapter-12.txt:40
./technical/911report/chapter-13.1.txt:40
./technical/911report/chapter-13.2.txt:0
./technical/911report/chapter-13.3.txt:47
./technical/911report/chapter-13.4.txt:30
./technical/911report/chapter-13.5.txt:24
./technical/911report/chapter-2.txt:2
./technical/911report/chapter-3.txt:149
./technical/911report/chapter-5.txt:1
./technical/911report/chapter-6.txt:67
./technical/911report/chapter-7.txt:1
./technical/911report/chapter-8.txt:13
./technical/911report/chapter-9.txt:0
./technical/911report/preface.txt:0
```

-c: Example 2
```
maxmendelson@Maxs-MBP docsearch % grep -c 'genomics' ./technical/biomed/gb-2002-3-11-research0061.txt
3
```

What it's doing: count occurrences of a specific term in documents
Why it's useful: useful for quantifying the presence of certain patterns. It's a quick way to get an overview of the frequency of a pattern without having to manually count matches.  

---

## Sources:
**For part 2, I asked ChatGPT:**  
Choose 4 interesting command-line options or alternate ways to use grep (these options are -i, -r, -l, and -c). Write a sentence or two about what each option does and why it’s useful.

**The output was:**  
Certainly! Here's an overview of the four grep command-line options you've chosen, along with explanations of what each does and why they are useful:

1. Option -i: Ignore Case
What it does: The -i option in grep makes the search case-insensitive. This means that it will match lines regardless of whether the characters in the search term are lowercase or uppercase.

Why it's useful: This is particularly helpful when you're not sure of the case of the text you're searching for or when the case is inconsistent. For example, searching for 'Error', 'ERROR', and 'error' would all yield the same results when using -i, ensuring that you don't miss relevant matches due to case differences.

2. Option -r: Recursive Search
What it does: The -r option enables recursive searching. This means grep will search through all directories and subdirectories starting from the given directory and match the specified pattern in all files.

Why it's useful: This is essential when working with projects with a complex directory structure, such as source code repositories. It allows you to quickly search through all files in all directories for a specific term, saving time and effort compared to manually searching each directory.

3. Option -l: List File Names
What it does: When using the -l option, grep only outputs the names of the files with matching lines, rather than the lines themselves. Each file name is listed only once.

Why it's useful: This is great for when you need to know which files contain a given pattern, but you don't need the actual content of the lines. It helps in quickly identifying relevant files, especially in large codebases or document collections.

4. Option -c: Count
What it does: The -c option makes grep count the number of lines that match the given pattern in each file, instead of displaying the matching lines.

**How I changed the output:**  
I modified some sentences and got rid of examples unnecessary to the explanation.
