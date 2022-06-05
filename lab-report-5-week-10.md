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
![expected Output of `483.md`](Lab%20Report%205/Expected-test-file483.png)
according to this picture, the Expected output should be: `[]`

  * **_Actual Output_ of `483.md`:** 
    * **_Left side_ is `my-markdown-parser`; _Right side_ is `cse15lsp22-markdown-parser`**
![actual Output of `483.md`](Lab%20Report%205/actual-output483.png)

  * Which implementation is correct and which is incorrect? 
    * comparing each actual output with the expected output, the implementation of `MarkdownParse.java` in `my-markdown-parser` is correct, and another implementation of `MarkdownParse.java` in `cse15lsp22-markdown-parser` is wrong. 
  
  * describe the bug (the problem in the code) in about 2-3 sentences. 
    * the bug in `cse15lsp22-markdown-parser/MarkdownParse.java` is:  

* For test-file `487.md`:
  * **_Expected Output_ of `487.md`:**
![](Lab%20Report%205/Expected-test-file487.png)
according to this picture, the Expected output should be: `[]`

  * **_Actual Output_ of `487.md`:** 
    * **_Left side_ is `my-markdown-parser`; _Right side_ is `cse15lsp22-markdown-parser`**
![](Lab%20Report%205/actual-output487.png)

  * Which implementation is correct and which is incorrect? 
    *  comparing each actual output with the expected output, the implementation of `MarkdownParse.java` in `cse15lsp22-markdown-parser` is correct, and another implementation of `MarkdownParse.java` in `my-markdown-parser` is wrong.

  * describe the bug (the problem in the code) in about 2-3 sentences. 
    * the bug in `my-markdown-parser/MarkdownParse.java` is:  
