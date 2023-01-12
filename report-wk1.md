# Lab Report: Week 1

### Installing Visual Studio Code
Download and install [Visual Studio Code](https://code.visualstudio.com/download) (VSCode). After finishing the installation process, open VSCode (you can use the WIN Key to open the Windows Start Menu, and search "Visual Studio Code"). Upon opening VSCode (and maybe closing out of some unnecessary first-time dialogues), you should see something like the screenshot below.

![image14](https://user-images.githubusercontent.com/46171121/211907206-719d09ca-c33c-4597-b2cb-a75c661e25c8.png)

### Remotely Connecting
To remotely connect via `ssh`, you first need to set up a password for your temporary course-specific account via the [UCSD ETS Account Lookup](https://sdacs.ucsd.edu/~icc/index.php) tool. Afterwards, open up a bash terminal, such as Git Bash. Once in Git Bash, enter `ssh <course-specific-account-username>@ieng6.ucsd.edu` and enter the password you set (you may have to wait up to 15 minutes for the password change to take effect). When you're done, you should see something like the screenshot below.

![image1](https://user-images.githubusercontent.com/46171121/211907242-3cbf304d-d0fa-45e9-8428-68a2d219a62a.png)

### Trying Some Commands
Now that you've remotely connected, try some commands. Some especially useful/basic commands you may want to mess around with are `ls`, `cd`, `mkdir`, `cat`. For example, the screenshot below shows the process of creating a directory in `~` named `hello`, going into that directory, creating a text file named `world.txt` with the contents `foobar`, and then printing out the contents of `world.txt`.

![image10](https://user-images.githubusercontent.com/46171121/211907276-7070f912-ebfc-455f-a857-8d839ae6e382.png)
