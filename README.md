This is the Github organization for **[EE241B](https://github.com/ucberkeley-ee241b)** @ UC Berkeley. 

> **Warning: Do not publicly share lab/project files online! Tool-related Makefiles and tcl scripts are proprietary!**

> Post questions & start discussions on **[Piazza](https://piazza.com/class/ixtn162b6t13f3)**! FAQs from particularly useful discussions will be compiled in this Github repo. 

---

Table of Contents
===================
1. [Software Overview](#software)
2. [Getting Access to EECS Compute Servers](#servers)
3. [Setting Up Github for Class](#github)
4. [Git Cheatsheet](#git)
5. [X2Go for Remote Access](#x2go)
6. [Getting Started with the Tools](#sourceme)

---

Software Overview <a name="software"></a>
===================

In your future IC design career, you will likely be using software from this *(non-exhaustive, not-quite-up-to-date-name-wise)* list:

* **Synopsys**
  * **VCS*** for functional verification
  * **Design Compiler (DC)*** for digital synthesis
  * **IC Compiler (ICC)*** for place and route
  * **PrimeTime*** for timing and power analysis 
  * **Liberty NXC*** for standard cell library characterization (Liberty file .lib generation)
  * **Library Compiler*** for creating standard cell libraries (Milkyway files) 
  * **Formality** for formal verification
  * **Hercules***
    * **DRC** for layout design rule checks
    * **LVS** for consistency checking between layout/schematic
  * **StarRC*** for parasitic extraction
* **Cadence**
  * **Virtuoso*** for "analog-y"/mixed-signal schematic design, layout, and verification
  * **Genus** for digital synthesis
  * **Innovus** (formerly SOC Encounter) for  place and route
* **Mentor Graphics Calibre**
  * **nmLVS** for consistency checking between layout/schematic
  * **nmDRC** for layout design rule checks 
  * **xRC** for parasitic extraction
* **HSpice*** for transistor characterization ([Simulation & Analysis Guide](https://cseweb.ucsd.edu/classes/wi10/cse241a/assign/hspice_sa.pdf), [Commands & Control Options](https://cseweb.ucsd.edu/classes/wi10/cse241a/assign/hspice_cmdref.pdf))
* **Matlab*** for design analysis

> Minimally, you will be using *'d software for EE241B ASIC labs and projects. If you're running into issues with the software required for this class, try consulting **[this page](http://inst.eecs.berkeley.edu/software.html)** for help on a given tool.

For homeworks and class projects, we will be using the 32nm educational library from Synopsys. 

---

Getting Access to EECS Compute Servers <a name="servers"></a>
===================

> Note: For students with BWRC accounts, consider doing your work on the BWRC compute servers *(You'll have access to all of the same tools!)* to lighten the load on instructional machines. You know which servers you can log in to. ;)

Students who need instructional accounts for the semester (and beyond) can acquire them by following the instructions on **[this page](https://inst.eecs.berkeley.edu/connecting.html)**.

To use the required software for this class, use your instructional account username/password to log in to one of the following Linux machines:

* hpse-9.eecs.berkeley.edu  (64-bit Centos Linux)
* hpse-10.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-11.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-12.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-13.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-14.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-15.eecs.berkeley.edu (64-bit Centos Linux)


**Ex:** `ssh -X yourusername@hpse-9.eecs.berkeley.edu`


If you're on Windows, download [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html), and start an **ssh** session with X11 forwarding enabled, and use *yourusername@hpse-9.eecs.berkeley.edu* for the host. If you're running into issues, refer back to detailed instructions **[here](https://inst.eecs.berkeley.edu/connecting.html)**.

> When logged in, you can use `top` to check how overloaded a machine is. If you think your session is running slowly, because the machine is being overused, consider switching to a different machine.

---

Setting Up Github for Class <a name="github"></a>
===================

We will be using Github to track lab & project files.

1. If you don't already have one, sign up for a **[Github account](https://github.com)**. 
2. **E-mail** me ([myfirst.lastname]@eecs.berkeley.edu) your **instructional account** username and **Github** username. I will then create a private repo (the name will be your instructional account or BWRC username) for you in the **[ucberkeley-ee241b](https://github.com/ucberkeley-ee241b)** organization. This is where you will push all of your lab/project files. 
3. After I've added you to the organization, setup automatic authentication with SSH. 
  1. SSH into one of the instructional compute servers (or a BWRC server), or connect with a remote connection (x2go) and open a terminal.
  2. *(If you don't already have one)* Generate a new **SSH key** via (detailed) instructions **[here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)**. *Note: Your e-mail should be the one you use on Github**.
    `ssh-keygen -t rsa -b 4096 -C "your_email_on_github@example.com"`
    [Press enter to use defaults.]
    `eval "$(ssh-agent -s)"`
    `ssh-add ~/.ssh/id_rsa`
  3. Add your SSH key to your **Github** account via instructions **[here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)**. You can get your SSH key with `cat ~/.ssh/id_rsa.pub`, and then copy & paste it into Github. 
4. Check to make sure that you setup everything correctly by cloning your (currently empty) private repo into your directory of choice. If it works, you're good to go! Just delete the repo from your directory for now.
  `git clone git@github.com:ucberkeley-ee241b/your-instructional-or-bwrc-user-name.git`
  `rm -rf your-instructional-or-bwrc-user-name`

> Note: When using SSH authentication, you need to clone/pull from **git@github.com**, and not https://github.com!

---

Git Cheatsheet <a name="git"></a>
===================

*(Modified from the CS250 Tutorial)*

| Git Command | Function | 
| ------------- | ------------- | 
| git clone (url) | Pulls a repository @ (url) from a remote server and creates a local version | 
| git init | Create a new repository in the current directory | 
| git remote add (origin) (url) | Associates (origin) with a repository @ (url) that you can push to |
| git remote set-url (origin) (url) | Update the (url) of (origin) |
| git pull (origin) (master) | Get updates from a branch (master) at the remote repository (origin) |
| git status | See what files have changed since the last commit. Also shows which branch you're on |  
| git log | See your commit history | 
| git diff | See what has changed | 
| git add (filename) | Stage a file for the next commit. Replace (filename) with **.** to add all updated files |  
| git commit -m "Message" | Commits staged files |  
| git push (origin) (master) | Push the latest commit to the (master) branch @ (origin) |  
| git checkout -- (filename) | Reverts a file to the last commited version |  
| git clean -dfx (dirname) | Reverts an entire directory to what it looked like @ the last commit |
| git branch (branch_name) | Create a new branch for tracking your work |
| git checkout (branch_name) | Switch to (branch_name) or an older commit (hash) for updating |
| git merge (branch_b) | If your current checked out branch is (branch_name), this merges (branch_b) into (branch_name) |
| git submodule add (url) | Adds the repo @ (url) into your project |
| git submodule update --init --recursive | (After pulling) Update repo submodules to latest contents |

> In general, you **do not** want to include generated files (log files, etc.) in the remote repository *(only source files!)*. To prevent them from cluttering the remote repo, add them to a **.gitignore** file in the top directory of your repo. i.e.: `*.log` will prevent any files with a *.log* extension from being uploaded to Github. You can also specify directories to exclude. 

> Sometimes, when merging branches or pulling from master, you'll run into merge conflicts. They must be fixed by going into the file(s) with merge conflicts and correcting the conflicts.

> For people just starting out with Git, check out these tutorials:
>   * [Git - The Simple Guide](http://rogerdudler.github.io/git-guide/) - Covers most of the commands you'll need
>   * [A Tutorial Introduction to Git](https://git-scm.com/docs/gittutorial)
>   * [CS250 Git Tutorial](https://inst.eecs.berkeley.edu/~cs250/sp17/handouts/tut1-git.pdf)

Git is kind of annoying to get used to. If you're stuck, just ask for help :). 

---

X2Go for Remote Access <a name="x2go"></a>
===================

If you're trying to ssh (+ X11 forward) into one of the compute servers remotely, interacting with any GUIs (= most apps used in the class) will be painfully slow (~1s response time). Instead, you might want to consider running GUI apps with X2Go. In previous incarnations of this class, NoMachine was used, but instructional servers have swapped over to X2Go. 

Instructions are found below:

1. Download [X2Go](https://wiki.x2go.org/doku.php/download:start)
2. Click through any welcome/intro screen, then click "New Session"
3. Name the session, and then set the host to be the server you wish to connect to. This should be one of the hpse servers (hpse-9.eecs.berkeley.edu through hpse-15.eecs.berkeley.edu). Also, set the login field to your username - this should be your inst username.
4. Modify the session type to your graphical interface of choice (KDE, GNOME, etc.)
5. In the "Connection" tab, you can set various image quality settings.
6. Click on the "Input/Output" tab. Here you can set various display settings, such as the resolution. We recommend you set "Bidrectional copy and paste" under the "Clipboard mode" section if you want to copy and paste between your machine and the x2go setting.
7. Hit OK once this is all set. Your new session should appear on the right side of your x2go window.
8. Click that session. You should be prompted to enter your password. Once this is done, press OK.
9. You should now be logged into the remote server. To open up a terminal, right-click the desktop and click "Open in Terminal" (tested for GNOME).
10. To log out, you can simply close the X2Go session window, or you can go to the manager window and click the "Suspend" button (this looks like a pause symbol). Your session will persist, so anything open when you suspend the session will be there when you log back in. If you want to terminate the session, press the "Terminate" button (which looks like a power on/off button). Since these are shared servers, you may want to terminate your session just to free up some memory for other users.

**For BWRC Account Holders**

Search the BWRC Wiki for "X2Go" to get instructions on how to get started. Opening up terminal, etc. still apply, obviously. You can also use other programs such as NoMachine and VNC.

---

Getting Started with the Tools <a name="sourceme"></a>
===================

Although you could probably get by in this class without looking at much more than the Makefiles associated with each lab, it's in your best interest to also look over the scripts in the (private to students) **[VLSI repo](https://github.com/ucberkeley-ee241b/cs250-vlsi-scripts)**. Feel free to ask questions about what you see! That way, when you're taping out your first digital chip, you'll have a better understanding of what parts of the scripts do what and what parts need to be customized... Even if you're doing a mostly analog chip, if you'll need a long scan chain or memory to store in ADC bits, you might end up using a digital flow to generate your logic. :)

> Note that the aforementioned *VLSI repo* isn't directly used in your labs -- that repo was adapted from CS250 (originally for use with a RISCV processor called rocket-chip). However, the scripts you'll be using in your labs are 95% the same. 

[To be continued... with how to setup .bashrc, etc.]
