# Lab Report 4

## 1. `links` of Repository
* My `markdown-pareser` Repository: [Bella - markdown-parser](https://github.com/BellaL6/markdown-parser) 
* szreik's `markdown-parser` Repository: [szreik - markdown-parser](https://github.com/szreik/markdown-parser)

## 2. Expected output vs. Actual output
* **_Expected_ output** showed in `VSCode Preview`:
  * Snippet 1: 
    ![Snippet 1 - expected output](Expected%20output/Snippet%201%20-%20EO.png)
    according to the preview of Snippet 1, the expected output should be: **_[`google.com, google.com, ucsd.edu]._**
    
  * Snippet 2:
    ![Snippet 2 - expected output](Expected%20output/Snippet%202%20-%20EO.png)
    according to the preview of Snippet 2, the expected output should be: **_[a.com, a.com(()), example.com]_**
    
  * Snippet 3:
    ![Snippet 3 - expected output](Expected%20output/Snippet%203%20-%20EO.png)  
    according to the preview of Snippet 3, the expected output should be: **_[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]_**

* **`code`** in `MarkdownParseTest.java` for those three markdown Snippets above:
  * **_Tests_** in My `MarkdownParseTest.java`
    ![Tests for Snippet 1to3](code%20in%20Tester/tests%20in%20Bella-Repo.png)
    
  * **_Tests_** in szreik's `MarkdownParseTest.java`
    ![Tests for Snippet 1to3](code%20in%20Tester/tests%20in%20szreik-Repo.png)
 
* **_Results_** of all three Snippet tests shown in `JUnit`:
  * All three results for tests in **my** `markdownParseTest.java` were **_fail_**:
    * test failture for Snippet 1:
      ![failture - Snippet1](code%20in%20Tester/failture-%20Snippet1%20-%20MyRepo.png)
 
    * test failture for Snippet 2:
      ![failture - Snippet2](code%20in%20Tester/failture-Snippet2%20-%20MyRepo.png)

    * test failture for Snippet 3: 
      ![failture - Snippet3](code%20in%20Tester/failture-Snippet3%20-%20MyRepo.png) 
      
   **Conclusion:** All three test failtures happened because expected outputs are **_unmatched_** with the actual outputs. No other Exception found.
    
    
  * All three results for tests in **szreik's** `markdownParseTest.java` were **_fail_**:
    * test failture for Snippet 1:
      ![failture - Snippet1](code%20in%20Tester/failture-Snippet1%20-%20OtherRepo.png) 
      
    * test failture for Snippet 2:
      ![failture - Snippet2](code%20in%20Tester/failture-Snippet2%20-%20OtherRepo.png)
      
    * test failture for Snippet 3: 
      ![failture - Snippet3](code%20in%20Tester/failture-Snippet3%20-%20OtherRepo.png)
      * more details for the test failture of Snippet 3:
        ![details - Snippet3](code%20in%20Tester/detail%20-%20otherRepo-Snippet3.png)
        
   **Conclusion:** For the first two test failtures, they happened because expected outputs are **_unmatched_** with actual outputs. No other Exception found. 
                   But for the third test failture, it happened because of the `java.lang.StringIndexOutOfBoundsException`. 
                   From the details of Snippet 3 failture, we observed that the beginning index is -2, but the correct beginning index should be 0.
                   

## 3. Answers Questions:
* 1.) Do you think there is a small (<10 lines) code change that will make
      your program work for snippet 1 and all related cases that use inline
      code with backticks? If yes, describe the code change. If not, describe
      why it would be a more involved change.
      
  * I don't think a small(<10 lines) code change will make my program work for snippet 1 and all related cases that use inline code with backtisks. 
    Because in the `VSCode Preview`, the `backtisks` does **NOT** show as other characters, which using `markdown.charAt(openBracket-1)=='backtisks'` 
    cannot find the `backtisks` out and successfully avoid adding link for its name with `backtisks` into the ArrayList `toReturn`. 
  * Moreover, according to the **expected output** shown in the `VSCode Preview`, 
   `backtisks` seens to change a character or some symbol into characters of name, which all characters 
    after the `backtisks` and before the next `backtisks` are **_part of the name of the link_**.  

* 2.) Do you think there is a small (<10 lines) code change that will make
      your program work for snippet 2 and all related cases that nest
      parentheses, brackets, and escaped brackets? If yes, describe the
      code change. If not, describe why it would be a more involved change.
      
  * I don't think a small(<10 lines) code change will make my program work for snippet 2 and all cases that nest parentheses, brackets, and escaped brackets. 
    Because those cases are not simple bracket/parenthese matching, it needs **Helper Method** for matching. 
  * According to the **expected output** in `VSCode Preview`,
    we can notice that: for the **_1st line_**, the `link` occurred in **between** the name within the 1st openBracket and the last closeBracket. It is because after the **_first `openBracket`_**,
    the link can be completed by a _complete brackets_ and a _complete parentheses_. Since the **3rd closeBracket** goes after **2nd openBracket**, and **2nd closeParen**
    goes after **1st openParen** right after the completed brackets. 
  * Same thing for the **_2nd line_** and **_third line_**, they also need **Helper Method** to find the complete bracket/parenthese matching
    to finish the `completed link`. The _ONLY special thing_ is that: in the **3rd line**, the `backslashs` has the same fact as `backtisks`, they both can change **all symbols(brackets, parentheses)**
    into simple characters used for _part of name_ or _part of link_. 
  * One of the **Helper Method** we can use is: **methods of the `Stack`**, such as: `push`, `pop`. 

* 3.) Do you think there is a small (<10 lines) code change that will make
      your program work for snippet 3 and all related cases that have
      newlines in brackets and parentheses? If yes, describe the code
      change. If not, describe why it would be a more involved change.
      
  * This case is a litle bit tricky, but I still don't think a small(<10 lines) code change will make my program work for snippet 3 and all related cases have newlines in brackets and parentheses.
  * According to the **expected output** in `VSCode Preview`, newlines in brackets and parentheses can have **different** effect. 
  * When the newline occurred right after the **first openParen** without any space between the `openParen` and the `firstChar`, and occurred again right after the **last character** 
    without any space between the `lastChar` and `closeParen`, then the newline will **NOT** has any impact to the result.
  * When the newline occurred in **between characters** for characters are _part of the name_, then the link format will be **destroyed** no matter what happened to the later part.
  * When the newline occurred in **between characters** for characters are _part of the link_, then the impact is depending on the format of newlines in between `openParen` and `closeParen`.
    * Even if **newlines** happened after the `openParen` and/or before the `closeParen`, if there are **no space** goes right after the **newline**, then the newline mentioned above will **NOT** has any impact. 
    * Otherwise, the link format will be **destroyed**.      




