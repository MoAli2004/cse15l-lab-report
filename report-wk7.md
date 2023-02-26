# Lab Report: Week 5

### CLDQ Procedure

1. Log into ieng6
    
    ![image](https://user-images.githubusercontent.com/46171121/221390780-d2161276-a94c-4dca-96ef-2f1aad4d1db0.png)
    
    *Keys pressed* `ssh cs15lwi23abd@ieng6.ucsd.edu<enter>`, `<password><enter>`
    
    The `ssh cs15lwi23abd@ieng6.ucsd.edu` command was not in the terminal history (yet), so I had to manually type it out. I was prompted for my account password, so I typed it in as well (of course, that's the section labeled `<password>` above, because I'm not going to put my password here).

2. Clone your fork of the repository from your Github account

    ![image](https://user-images.githubusercontent.com/46171121/221391853-e6e03956-0de0-4e39-ac78-ec6d09f0fded.png)

    *Keys pressed* `git clone <shift + ins><enter>`
    
    I had my git fork repository's URL (the ssh one) copied in the clipboard, so I pressed `<shift + ins>` to paste it into the terminal (`<shift + ins>` is the paste hotkey in Git Bash).

3. Run the tests, demonstrating that they fail

    ![image](https://user-images.githubusercontent.com/46171121/221391896-b01244de-26e6-447a-8954-5ac7514848cf.png)

    *Keys pressed* `cd c<tab><enter>`, `javac -cp ".:lib/*" *.java<enter>`, `java -cp ".:lib/*" org.junit.runner.JUnitCore ListExamplesTests<enter>`

    Since there was only one directory beginning with the character "c", I could press `<tab>` to autocomplete the rest of the name (I named my git fork `cse15l-lab7`, so the directory name was `cse15l-lab7`). I had to manually type out the commands `javac -cp ".:lib/*" *.java` and `java -cp ".:lib/*" org.junit.runner.JUnitCore ListExamplesTests`. To speed things up a bit, I wrote `lib/*` in the classpath, taking advantage of the wildcard to save time from writing out the full .jar filenames.

4. Edit the code file to fix the failing test

    ![image](https://user-images.githubusercontent.com/46171121/221391089-69ca86e1-9e42-4f15-b3f3-5570313b00c2.png)
    ![image](https://user-images.githubusercontent.com/46171121/221391101-f139ce27-6669-4733-8d22-1ed370a446c2.png)
    ![image](https://user-images.githubusercontent.com/46171121/221391115-4b94cf18-df30-46f0-8000-c4ee52553ea1.png)

    *Keys pressed* `nvim L<tab>.j<tab><enter>`, `:43<enter>`, `er2:wq<enter>`
    
    I used Neovim instead of GNU nano to edit the code because Neovim (a fork of Vim) supports commands that make editing a bit faster. To open up the text file with the `nvim ListExamples.java` command, I again used `<tab>` to autocomplete the name (there are two files named `ListExamples`, so I also had to type `.j<tab>` to select the .java file). Then in Neovim, I used the following commands: `:43` to jump to line 43, `e` to jump to the end of the current word (`index1`), `r2` to replace the character with `2`, and `:wq` to save and exit.

5. Run the tests, demonstrating that they now succeed

    ![image](https://user-images.githubusercontent.com/46171121/221391308-f14d93e7-6fd2-4c79-9bac-5343e9df088c.png)

    *Keys pressed* `<up><up><up><enter>`, `<up><up><up><enter`
    
    Both the compile and run commands were already run previously (step 3), so I could just go back to them with three <up> presses.

6. Commit and push the resulting change to your Github account (you can pick any commit message!)
  
    ![image](https://user-images.githubusercontent.com/46171121/221391967-ca04c16a-80f0-4c37-9989-1fd856e31379.png)
  
    *Keys pressed* `git stage .<enter>`, `git commit -m "Fix merge method"<enter>`, `git push<enter>`
  
    None of the git commands were stored in the terminal history or clipboard, so I just had to manually type them all out.

  
