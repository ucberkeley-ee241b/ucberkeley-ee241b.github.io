> **Warning: Do not publicly share lab/project files online! Tool-related Makefiles and tcl scripts are proprietary!**

> Post questions & start discussions on **[Piazza](https://piazza.com/class/ixtn162b6t13f3)**! FAQs from particularly useful discussions will be compiled in this Github repo. 

Table of Contents
===================
1. [Software Overview](#software)
2. [Getting Access to EECS Compute Servers](#servers)
3. [Setting Up Github for Class](#github)


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

> Minimally, you will be using *'d software for EE241B ASIC labs and projects. 

Getting Access to EECS Compute Servers <a name="servers"></a>
===================

> Note: For students with BWRC accounts, consider doing your work on the BWRC compute servers *(You'll have access to all of the same tools!)* to lighten the load on instructional machines.

Students who need instructional accounts for the semester (and beyond) can acquire them by following the instrucions on **[this page](https://inst.eecs.berkeley.edu/connecting.html)**.

To use the required software for this class, use your instructional account username/password to log in to one of the following Linux machines:

* hpse-9.eecs.berkeley.edu  (64-bit Centos Linux)
* hpse-10.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-11.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-12.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-13.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-14.eecs.berkeley.edu (64-bit Centos Linux)
* hpse-15.eecs.berkeley.edu (64-bit Centos Linux)


**Ex:** `ssh -X yourusername@hpse-9.eecs.berkeley.edu`


If you're on Windows, download [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html), and start an **ssh** session with X11 forwarding enabled, and use *yourusername@hpse-9.eecs.berkeley.edu* for the host. 

> You can use `top` to check how overloaded a machine is. If you think your session is running slowly, because the machine is being overused, consider switching to a different machine.

Setting Up Github for Class <a name="github"></a>
===================

We will be using Github to track lab & project files.

1. If you don't already have one, sign up for a **[Github account](https://github.com)**. 
2. **E-mail** me ([myfirst.lastname]@eecs.berkeley.edu) your **instructional account** username and **Github** username. I will then create a private repo (the name will be your instructional account or BWRC username) for you in the **ucberkeley-ee241b** organization. This is where you will push all of your lab/project files. 
3. After I've added you to the organization, setup automatic authentication with SSH. 
  1. SSH into one of the instructional compute servers (or a BWRC server).
  2. *(If you don't already have one)* Generate a new **SSH key** via (detailed) instructions **[here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)**. *Note: Your e-mail should be the one you use on Github**. 
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email_on_github@example.com"
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_rsa
    ```
  3. Add your SSH key to your **Github** account via instructions **[here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)**. You can get your SSH key with `cat ~/.ssh/id_rsa.pub`, and then copy & paste it into Github. 
4. Check to make sure that you setup everything correctly by cloning your (currently empty) private repo into your directory of choice. If it works, you're good to go! Just delete the repo from your directory for now.
  ```
  git clone git@github.com:ucberkeley-ee241b/your-instructional-or-bwrc-user-name.git
  rm -rf your-instructional-or-bwrc-user-name
  ```