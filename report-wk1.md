# Lab Report: Week 1

### Installing Visual Studio Code
Download and install [Visual Studio Code](https://code.visualstudio.com/download) (VSCode). After finishing the installation process, open VSCode (you can use the WIN Key to open the Windows Start Menu, and search "Visual Studio Code"). Upon opening VSCode (and maybe closing out of some unnecessary first-time dialogues), you should see something like the screenshot below.

![image14](https://user-images.githubusercontent.com/46171121/211907206-719d09ca-c33c-4597-b2cb-a75c661e25c8.png)

To open a terminal in VSCode, you can press ``CTRL + ` `` to show the terminal, or ``CTRL + SHIFT + ` `` to create a new terminal instance. A new pane at the bottom of VSCode should open up that resembles the screenshow below.

![image](https://user-images.githubusercontent.com/46171121/214731852-60df6c7a-7fce-487f-b307-62d1fbffa82b.png)

### Remotely Connecting
To remotely connect via `ssh`, you first need to set up a password for your temporary course-specific account via the [UCSD ETS Account Lookup](https://sdacs.ucsd.edu/~icc/index.php) tool. Afterwards, open up a bash terminal, such as Git Bash. Once in Git Bash, enter `ssh <course-specific-account-username>@ieng6.ucsd.edu` and enter the password you set (you may have to wait up to 15 minutes for the password change to take effect). When you're done, you should see something like the screenshot below.

![image1](https://user-images.githubusercontent.com/46171121/211907242-3cbf304d-d0fa-45e9-8428-68a2d219a62a.png)

### Trying Some Commands
Now that you've remotely connected, try some commands. Some especially useful/basic commands you may want to mess around with are:
* `ls` lists the contents of a directory
* `cd` changes into a given directory
* `mkdir` creates a directory with a given name
* `cat` outputs text

For example, the following sequence of commands creates a directory in `~` named `hello`, changes into that directory, creates a text file named `world.txt` with the contents `foobar`, and then prints out the contents of `world.txt`:
1. `mkdir hello` to make a directory named `hello/`

![image](https://user-images.githubusercontent.com/46171121/214733028-7ba9c080-5be8-4f4e-8a9e-89c72a322316.png)

2. `ls` to show that the `hello/` directory was created

![image](https://user-images.githubusercontent.com/46171121/214733070-7a255787-4bfb-4bfa-9843-ac51823183ce.png)

3. `cd hello` to change into the `hello/` directory

![image](https://user-images.githubusercontent.com/46171121/214733114-6c00f8eb-7524-4f22-8e1e-2362e5d0ecc9.png)

5. `cat > world.txt` to output the text provided by the user into a new file named `world.txt`

![image](https://user-images.githubusercontent.com/46171121/214733243-adbb4c34-5668-47c8-a599-445aa5e16e9f.png)

5. `ls` to show that the `world.txt` file was created

![image](https://user-images.githubusercontent.com/46171121/214733300-826928f9-cb08-440e-a979-1766f6cc5757.png)

6. `cat world.txt` to output the text in the file to the terminal

![image](https://user-images.githubusercontent.com/46171121/214733344-1a9e3cb4-f496-4d24-ad2a-1e4a543e7eec.png)
