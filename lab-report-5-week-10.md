# Lab Report 5

## 1. How you found the tests with different results?
* I used `vimdiff` on the results of running a bash for loop.
* By creating `results.txt` on two different repositories, those two `.txt` files contains **all outputs** of all `*.md` files inside the **_test-files_** folder, through the provided implementation and our own implementation of `MarkdownParse.java`. 

## 2. Provide a link to the test-file with different-results:
* [test-file483.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/483.md?plain=1)
* [test-file487.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/487.md?plain=1)

## 3. Description to each test:
* For test-file `483.md`:
  * **_Expected Output_ of `483.md`:**
    * ![expected Output of `483.md`](Lab%20Report%205/Expected-test-file483.png)
      according to this picture, the Expected output should be: `[]`

  * **_Actual Output_ of `483.md`:** 
    * **_Left side_ is `my-markdown-parser`; _Right side_ is `cse15lsp22-markdown-parser`**
      ![actual Output of `483.md`](Lab%20Report%205/actual-output483.png)

  * **Which implementation is correct and which is incorrect?**
    * comparing each actual output with the expected output, the implementation of `MarkdownParse.java` in `my-markdown-parser` is correct, and another implementation of `MarkdownParse.java` in `cse15lsp22-markdown-parser` is wrong. 
  
  * **describe the bug (the problem in the code) in about 2-3 sentences.** 
    * the bug in `cse15lsp22-markdown-parser/MarkdownParse.java` is:  
      * The bug occurred in the `ArrayList<String> getLinks(String markown)`. In this static method, this implementation of `MarkdownParse.java` considered cases when the `linkname` contains characters such as: `/`, which will not show in the `Preview`. But it ignores the case when the `linkname` is empty. When the `linkname` is empty, then this whole link will **not** be counted as a **formal link** and will **_NOT_** include into the **output list**.   
      * Below is the part inside the `MarkdownParse.java` which we should edit and fix: 
        ![cse15lsp22-codeToChange](https://github.com/BellaL6/cse15l-lab-reports/blob/main/Lab%20Report%205/cse15lsp22-markdown-parser-code.png)

* For test-file `487.md`:
  * **_Expected Output_ of `487.md`:**
    * ![expected Output of `487.md`](Lab%20Report%205/Expected-test-file487.png)
      according to this picture, the Expected output should be: `[]`

  * **_Actual Output_ of `487.md`:** 
    * **_Left side_ is `my-markdown-parser`; _Right side_ is `cse15lsp22-markdown-parser`**
      ![actual Output of `487.md`](Lab%20Report%205/actual-output487.png)

  * **Which implementation is correct and which is incorrect?**
    *  comparing each actual output with the expected output, the implementation of `MarkdownParse.java` in `cse15lsp22-markdown-parser` is correct, and another implementation of `MarkdownParse.java` in `my-markdown-parser` is wrong.

  * **describe the bug (the problem in the code) in about 2-3 sentences.**
    * the bug in `my-markdown-parser/MarkdownParse.java` is:
      * The bug occurred in the `ArrayList<String> getLinks(String markown)`. In this static method, my implementation of `MarkdownParse.java` didn't consider the case when the link **_contains other characters**_(EX: `/`) that will **change** the whole link format to a _simple String_. So when the `link` didn't contain other format issues that will **change** the link to an `image` or basically **cannot form** to a `link`, the output will contain this `link`. 
      * Below is the part inside the `MarkdownParse.java` which we should edit and fix: 
        ![my-codeToChange](https://github.com/BellaL6/cse15l-lab-reports/blob/main/Lab%20Report%205/my-markdown-parser-code.png)   
