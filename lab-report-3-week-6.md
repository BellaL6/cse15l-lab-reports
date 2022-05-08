# Lab-Report-3

### 1. Streamlining ssh Configuration
* **Show** the  `.ssh/config` file and **how to edit** it with VScode and other programs:
  * Create a **_empty_** `.ssh/config` file:
   ![Empty config](Choice%201/show%20empty%20config%20file.png)
  * **Edit** the `.ssh/config` file with **TextEdit**:
   ![TextEdit edit](Choice%201/edit%20config%20in%20TextEdit.png)
  * Show the **_first edited_** `.ssh/config` file:
   ![Output after TextEdit](Choice%201/show%20output%20config%20after%20TestEdit.png)
  * **Edit** the `.ssh/config` file with **GNU nano**:
   ![nano edit](Choice%201/edit%20config%20in%20GNU%20nano.png)
  * Show the **_final edited_** `.ssh/config` file:
   ![Output after nanoEdit](Choice%201/show%20output%20config%20after%20nanoEdit.png)
* used the `ssh` command to **_login_** my account with **just using** the alias `ieng6`:
![login with **ieng6**](Choice%201/ssh%20login%20account%20with%20alias.png)
* used the `scp` command to **_copy_** the file `FileCopy.java` to my account with **just using** the alias `ieng6`:
![copy file to account with **ieng6**](Choice%201/scp%20copy%20file%20with%20alias.png)
  * Show the **_location_** and **_file contents_** in my account after using `scp`:
   ![Output after using **scp**](Choice%201/output%20from%20account%20after%20scp.png)


### 2. Setup Github Access from ieng6
* **location** of _public key_ I made is stored on **Github** :
  * On your Github, when clicking on your account portrait (which is in the **upper right corner**), we can see `Settings`: 
   ![Settings](Choice%202/click%20setting.png)
  * Inside the `Settings`, find the `SSH and GPG keys` on the **left-side menu**, and click it:
   ![SSH and GPG keys](Choice%202/click%20SSH%20and%20GPG%20keys.png)
  * Then we will see the `SSH keys` and `GPG keys`, the location of _public key_ was the `SSH keys`:  
   ![public key on Github](Choice%202/public%20key%20stored%20on%20Github.png)
* **location** of _public key_ I made is stored in my **user account** :
  * After using `cd` to change the directory to `.ssh`, we can use `ls` to view what files contain in the `ssh` account. Moreover, the public key is contained in the file `id_ed25519.pub` in the `.ssh` account: 
   ![public key in account](Choice%202/location%20of%20storing%20pub.%20key%20in%20account.png)
* **location** of _private key_ which I made is stored in my **user account** :
  * Similar to the process of finding the public key in our account: using `cd` to change the directory to `.ssh`. Then when we use `ls` to view what files contain in our account, we will notice that there are `id_ed25519.pub` and `id_ed25519`. Since we have told the public key was stored in `id_ed25519.pub`, we know `id_ed25519` is the location where the private key was stored in our account:
   ![private key in account](Choice%202/location%20of%20storing%20priv.key%20in%20account.png)
* running `git` commands to **_commit_** and **_push_** a change to **Github** with _logged into `ieng6` account_ :
  * After get into your repository in Github(suggest to `open in Visual Studio Code` through **Github Desktop**), type `git status` in the terminal
  * Then it will tell you what files have modified and **not yet** commit and push by **highlighting** them in _red_.
  * Then we can type `git add <fileName>` (fileName should _match_ with the one it provided) add **all** not modified files together
  * type `git commit -m "<any description you want>" to commit your files
  * it will tell you the analysis of changes. Then typing `git push origin main` to push all commited files to Github. Below is the process I did:
   ![running git to commit and push](Choice%202/run%20git%20to%20push%20success.png)     
* link for the **_resulting commit_** :
[resulting-commit](https://github.com/BellaL6/markdown-parser/commit/e8c49a69268068d0cd6b64d2ffc2dd6b282fedee)

### 3. Copy whole directories with `scp -r`
* Before using `scp` to copy the directory to our account, using `pwd` to check the **working directory** and using `ls` to check all files we have inside the directory which we are going to copy. 

* **_Method 1_**: using `scp -r . cs15lsp22zz@ieng6.ucsd.edu:~/<directory>`, remember to change `zz` with your _account specific number_.
  * This is how it looks like after using the method 1 `scp`: 
   ![Output-methog 1](Choice%203/scp%20copy%20directory%20to%20remote%201.1.png)
   ![Output-method 1 continue](Choice%203/scp%20copy%20directory%20to%20remote%201.2.png)
  * Then we can **login** the account with `ssh ieng6` to check: 1. whether the copied directory _existed_ by using `ls`, and 2. whether the copied directory _contains all files_ it had in our local device by using `ls <directory>`:
   ![directory shown in ssh](Choice%203/output%20markdown-parser%20in%20ssh%20account1.png)
  * **Inside** the account, we are going to _compile_ and _run_ the `MarkdownParse.java` and `MarkdownParseTest.java`. First, we need to use `cd` to change the directory to `markdown-parser`.
  * Then **compile** `MarkdownParse.java` by using `javac MarkdownParse.java`, and **run** it to **test a _`md` file_** by using `java MarkdownParse <test Name.md>`.
  * For **compiling** the _JUnit test_, we need to type `javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java`; For **running** it, we need to type `java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest`. Below is how it will run:
   ![compile and run in ssh - Method 1](Choice%203/compile%20and%20run%20tests%20after%20scp1.png) 

* **Method 2**: using `scp -r . ieng6:<directory>`. 
  * This is how it looks like after using the method 2 `scp`:
   ![Output-method2](Choice%203/scp%20copy%20directory%202.1.png)
   ![Output-method2 continue](Choice%203/scp%20copy%20directory%202.2.png)
  * Same thing to **login** the account with `ssh ieng6` to check: 1. whether the copied directory _existed_ by using `ls`, and 2. whether the copied directory _contains all files_ it had in our local device by using `ls <directory>`:
   ![directory shown in ssh](Choice%203/output%20markdown-parser%20in%20ssh%202.png)
  * **Inside** the account: First, use `cd` to change the directory to `markdown-parser`.
  * Then **compile** `MarkdownParse.java` by using `javac MarkdownParse.java`, and **run** it to **test a _`md` file_** by using `java MarkdownParse <test Name.md>`.
  * **compiling** the _JUnit test_ by typing `javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java`; and **run** it by typing `java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest`. Below is how it will run:
   ![compile and run in ssh - Method 2](Choice%203/compile%20and%20run%20test%20in%20ssh%202.png)

* **Method 3**: using `scp -r *.java *.md lib/ cs15lsp22zz@ieng6.ucsd.edu:<directory>` to copy java files, md files and lib ONLY; remember to change `zz` to your account specific number.
  * This is how it looks like after using the method 3 `scp`:
   ![Output-method3](Choice%203/scp%20only%20javaFile%20mdFile%20and%20lib%20from%20directory%20to%20ssh%203.png)
  * **login** the account with `ssh ieng6` to check: 1. whether the copied directory _existed_ by using `ls`, and 2. whether the copied directory _contains all files_ it had in our local device by using `ls <directory>`:
   ![directory shown in ssh](Choice%203/output%20markdown-parser%20in%20ssh%203.png)
  * **Inside** the account: First, use `cd` to change the directory to `markdown-parser`.
  * Then **compile** `MarkdownParse.java` by using `javac MarkdownParse.java`, and **run** it to **test a _`md` file_** by using `java MarkdownParse <test Name.md>`.
  * **compiling** the _JUnit test_ by typing `javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java`; and **run** it by typing `java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest`. Below is how it will run:
   ![compile and run in ssh - method 3](https://github.com/BellaL6/cse15l-lab-reports/blob/main/Choice%203/compile%20and%20run%20tests%203.png)

* **Last Method**: copy the directory and login the account in **one line**; then inside the account: compile and run tests in **one line**:


