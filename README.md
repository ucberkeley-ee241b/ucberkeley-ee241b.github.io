> **Warning: Do not publicly share lab/project files online! Tool-related Makefiles and tcl scripts are proprietary!**

> Post questions & start discussions on **[Piazza](https://piazza.com/class/ixtn162b6t13f3)**! FAQs from particularly useful discussions will be compiled in this Github repo. 

Table of Contents
===================
1. [Software Overview](#software)
2. [Getting Access to EECS Compute Servers](#servers)
3. [Setting Up Github for Class](#github)
4. [Git Cheatsheet](#git)
5. [NoMachine for Remote Access](#nomachine)


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
* **HSpice*** for transistor characterization
* **Matlab*** for design analysis

> Minimally, you will be using *'d software for EE241B ASIC labs and projects. If you're running into issues with the software required for this class, try consulting **[this page](http://inst.eecs.berkeley.edu/software.html)** for help on a given tool.

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

Setting Up Github for Class <a name="github"></a>
===================

We will be using Github to track lab & project files.

1. If you don't already have one, sign up for a **[Github account](https://github.com)**. 
2. **E-mail** me ([myfirst.lastname]@eecs.berkeley.edu) your **instructional account** username and **Github** username. I will then create a private repo (the name will be your instructional account or BWRC username) for you in the **[ucberkeley-ee241b](https://github.com/ucberkeley-ee241b)** organization. This is where you will push all of your lab/project files. 
3. After I've added you to the organization, setup automatic authentication with SSH. 
  1. SSH into one of the instructional compute servers (or a BWRC server).
  2. *(If you don't already have one)* Generate a new **SSH key** via (detailed) instructions **[here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)**. *Note: Your e-mail should be the one you use on Github**.
    `ssh-keygen -t rsa -b 4096 -C "your_email_on_github@example.com"`
    [Press enter to use defaults.]
    `eval "$(ssh-agent -s)"`
    `ssh-add ~/.ssh/id_rsa`
  3. Add your SSH key to your **Github** account via instructions **[here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)**. You can get your SSH key with `cat ~/.ssh/id_rsa.pub`, and then copy & paste it into Github. 
4. Check to make sure that you setup everything correctly by cloning your (currently empty) private repo into your directory of choice. If it works, you're good to go! Just delete the repo from your directory for now.
  `git clone git@github.com:ucberkeley-ee241b/your-instructional-or-bwrc-user-name.git`
  `rm -rf your-instructional-or-bwrc-user-name`

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

> In general, you **do not** want to include generated files in the remote repository *(only source files!)*. To prevent them from cluttering the remote repo, add them to a **.gitignore** file in the top directory of your repo. i.e.: `*.log` will prevent any files with a *.log* extension from being uploaded to Github. You can also specify directories to exclude. 

> Sometimes, when merging branches or pulling from master, you'll run into merge conflicts. They must be fixed by going into the file(s) with merge conflicts and correcting the conflicts.

> For people just starting out with Git, check out these tutorials:
>   * [Git - The Simple Guide](http://rogerdudler.github.io/git-guide/) - Covers most of the commands you'll need
>   * [A Tutorial Introduction to Git](https://git-scm.com/docs/gittutorial)
>   * [CS250 Git Tutorial](https://inst.eecs.berkeley.edu/~cs250/sp17/handouts/tut1-git.pdf)

Git is kind of annoying to get used to. If you're stuck, just ask for help :). 

NoMachine for Remote Access <a name="nomachine"></a>
===================

If you're trying to ssh (+ X11 forward) into one of the compute servers remotely, interacting with any GUIs (= most apps used in the class) will be painfully slow (~1s response time). Instead, you might want to consider running GUI apps with NoMachine. 

---

**For Instructional Account Holders**

Instructions (from CS250) are found below:

1. Download [NoMachine](http://www.nomachine.com/download-beta.php).
2. Click through the welcome/intro screens, then click "Add a computer".
3. Name the connection and set the protocol as SSH.
4. For "Host", enter any of the instructional server addresses listed above.
5. Click "Advanced", and select "Use the NoMachine login".
6. Check the box marked "Use an alternate server key", then open the file browser and select the key for the **hpse** instructional machines, which can be downloaded **[here](http://inst.eecs.berkeley.edu/pub/nxkeys/hpse.client.id_dsa.key)**. 
7. If a message appears asking about server authenticity, click "Continue".
8. Log in with your instructional account username and password.
9. Click "New Virtual Desktop", and create a new GNOME virtual desktop.
10. You should now be logged into the compute server. To open up a terminal window once you've connected:
  * On the top menu bar, click on Applications - Accessories - Terminal.
  * You can drag the Terminal icon from the drop down menu to a blank spot on the menu bar to create a shortcut.
11. To log out, simply close the NoMachine window. You will see a prompt to either suspend or terminate your session. 

> *Please make a habit of terminating your NX sessions when you are done working to conserve memory on the servers.*

> If you are having issues with NoMachine, you can try other (older) NoMachine clients that may work better on your personal machine:
>   * [OpenNx](http://opennx.net/download.html)
>   * [NX Client](http://www.nomachine.com/download.php) - will not work on Mac OS 10.7 or later
> In addition, instructional computing maintains a help document for NX that can be found at [here(https://inst.eecs.berkeley.edu/cgi-bin/pub.cgi?file=nx.help).

---

**For BWRC Account Holders**

Search the Wiki for "NoMachine" to get instructions on how to get started. 
