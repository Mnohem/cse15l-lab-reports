Preface
------------
Some steps may be different than expected, as my operating system is a distribution of Linux, specifically Void Linux.

## Installing VScode
- VScode is available on my package manager, so to install it I did `$ sudo xbps-install vscode`
- The executable is installed as /usr/bin/code-oss \
![Screenshot](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/screenshot-2022-04-09-14%3A10%3A14.png)

## Remotely Connecting
- After I changed my password, I logged in using `$ ssh cs15lsp22zzz@ieng6.ucsd.edu` where zzz was replaced with my specific three characters. \
![Screenshot](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/slurped-2022-03-31-12%3A26%3A12.png)

## Trying some commands
- After logging in, I tried some commands to see what files were on the remote server.
- I did `$ ls -al` in my home folder and the root folder. \
![Screenshot](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/slurped-2022-03-31-12%3A45%3A12.png)

## Moving files with scp
- I first create a file to move so I did `$ touch test`, where test is the name of my file.
- Then I did `$ scp test cs15lsp22apx@ieng6.ucsd.edu:~/` to copy the file to the remote server.
- I connected and checked for the file. \
![Screenshot](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/slurped-2022-04-09-14%3A16%3A06.png)

## Setting the SSH key
- `$ ssh-keygen` to generate a new ssh key
- Create a .ssh directory on the remote server for the next step.
- `$ scp .ssh/id_rsa.pub cs15lsp22apx@ieng6.ucsd.edu:~/.ssh/authorizedkeys` to make the newly created public key an authorized key on the remote server \
- I can now connect with no password
![Screenshot](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/slurped-2022-04-09-14%3A17%3A38.png)

## Optimizing Remote Running
If you want to compile and run a locally written java program on the remote server, this is all you need to do \
- `$ scp Program.java cs15lsp22apx@ieng6.ucsd.edu:~/` 
- `$ ssh cs15lsp22apx@ieng6.ucsd.edu "javac Program.java; java Program"`
![Screenshot](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/slurped-2022-03-31-13%3A18%3A21.png)
