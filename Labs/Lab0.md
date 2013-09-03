# Lab 0: Logisim and Git setup

[Logisim](http://ozark.hendrix.edu/~burch/logisim/) is a circuit simulator. Download it!

Git is a popular distributed version control system that we will use in this course. Git tracks changes (commits) to a project (repository) over time and decouples recording changes from publishing (pushing) changes.

In this lab, you will download, install and configure Git so that you can commit (record changes) and push (submit changes) privately to your choice of project host (Bitbucket or Github), and practice Git basics. While the professor's Git repository is publicly available, you will make your Git repository private on the project host but share it with me. Therefore, anything you submit to project host for this repository will be visible only to you and me, but nobody else.

These instructions assume that you are using Windows, but should work fine on Mac or Linux. All errors and omissions are mine. Feel free to share your improvements to these instructions (pull requests are welcome).

First, [download and install Git from here](http://git-scm.com). With one exception, the default settings in the installer are fine, so click *Next*, *Continue*, or *Finish* to move along. When it is an option, be sure to select **Run Git and included Unix tools from the Windows Command Prompt**. This will allow you to use Git outside Git Bash if you wish to do so.

Also, [download and install TortoiseGit](http://code.google.com/p/tortoisegit/). The default settings in that installer are fine, so click to move the installer along. TortoiseGit allows you to commit and push your work directly to the project host from Windows Explorer, and also includes a nice diff viewer and merge tool. Similar tools for Mac/Linux include GitX, KDiff3, and Meld.

Once Git is installed, you will need to open the command prompt and keep it open for the duration of this lab. From the Start Menu, open Git Bash: **Start -> All Programs -> Git -> Git Bash**. In Mac/Linux, open **Terminal**. You will see a window with text inside; this is the command prompt. 

Git doesn't know you (and don't worry if you don't know Git just yet), so introduce yourself to Git. In the command prompt, tell Git who you are (use your name and school email address). Type in something like the following (replace my name and email with yours).

	git config --global user.name "Joey Lawrance"    # Use your name
	git config --global user.email lawrancej@wit.edu # Use your email

You will need to set up SSH keys now so you can easily submit your work to the project host that you will soon choose. SSH keys allow you to authenticate and send changes securely to a project host without the trouble of Git asking you to enter a password all the time. Type in the following command to generate SSH public/private keys.

	ssh-keygen -t rsa

The SSH key generator will ask several questions that you can ignore; just go with the defaults by pressing Enter until you're back to the command prompt.

Next, copy the public key to the clipboard using one of the commands below. Remember: the public key is what you share with others, and the private key is what you never share with anyone but the NSA. ;-)

	cat ~/.ssh/id_rsa.pub > /dev/clipboard # On Windows
	cat ~/.ssh/id_rsa.pub | pbcopy         # On Mac OS X
	cat ~/.ssh/id_rsa.pub | xclip          # On Linux

At this point, you are done downloading, installing and configuring Git. Yay!

Next, choose a project host, but don't create an account just yet (read on for why). The choices are [Bitbucket](http://bitbucket.org) or [Github](http://github.com). I use both project hosts, but you can use just one. Bitbucket gives you free private repositories by default, so it's easy to set up. However, Github has a much slicker interface but requires that you [request private repositories for educational purposes as a student](http://github.com/edu). Github's turn around time is short, but the start of a semester is the busiest time for this. If you choose Github, after you create an account, you will [request private repositories as a student](http://github.com/edu) and then make the repository you create private later. You need to ensure that your repository is private, otherwise I won't post feedback to you.

Did you choose a project host? Great! Go ahead and create an account using your *@wit.edu* email address and real name. Once you set up an account successfully, [complete this form](https://docs.google.com/forms/d/1lsSvVQVRlnIKl8qp5sSWwy-BgxyqnYGEvDzGLoQXV28/viewform) so that I know where to look for your work. If you feel like it, you can set up a [Gravatar](http://en.gravatar.com/) with your *@wit.edu* email address so that everyone can associate your user name with your face.

You will need to share the public SSH key you created earlier with the project host. If you haven't copy/pasted anything in the interim, you should be good to go. Bitbucket users: navigate to your user (in the upper right corner) -> Manage account -> SSH keys; [Github users go here](https://github.com/settings/ssh). Click Add key, and then paste in your public SSH key into the key field. For the title, use a nickname for your machine (e.g., laptop).

At this point, you have set up your account on a project host. Huzzah!

You now need to create a Git repository on your machine to save (commit) your work and get material from me. Copy/paste the following commands into the command prompt (don't even think about typing it in manually). Speaking of which, to paste into a command prompt in Windows, press Insert on the keyboard (Ctrl-V doesn't work); if that doesn't work, right click the command prompt window title, select Edit -> Paste.

	git init COMP278 # Create local git repository
	cd COMP278
	git remote add upstream https://github.com/lawrancej/COMP278.git
	git pull upstream master # Pull from the professor (upstream)

If you see something like the following, then everything worked fine.

	remote: Counting objects: 12, done.
	remote: Compressing objects: 100% (10/10), done.
	remote: Total 12 (delta 1), reused 0 (delta 0)
	Unpacking objects: 100% (12/12), done.

The commands you just entered cloned a copy of my repository onto your machine in the COMP278 folder. You can access this folder in the Windows File Explorer by navigating to Desktop -> Your User Name -> COMP278. You can also bring up this folder by typing in `start .` at the command prompt. Those of you in the know may ask: why not just do a git clone instead? The answer: because I want to be `upstream`, not `origin`. 

Now let's create a remote private repository on the project host to submit your work. On [Bitbucket](https://bitbucket.org/repo/create) or [Github](https://github.com/new), create a new empty **private** repository called **COMP278**. Aside from setting the repository private, don't play around with the other settings, just go with the defaults (DO NOT initialize the repository with a README).

Once created, the project host will offer instructions for the command prompt (Bitbucket users: pretend you are starting from scratch). We only need to run one command: find the line in the instructions that says `git remote add origin ...` and copy/paste it into the command prompt and press enter. Then, type in the following at the command prompt and press enter.

	git push -u origin master

If it asks for your password, you didn't set up the SSH keys properly. If this happens, don't fret, you can still type in your project host password and press Enter (or go back and fix it). By the way, don't expect to see anything as you type in your password, nothing will appear (it's not broken, it's a security feature).

If all goes well, when you reload your Bitbucket or Github repository page, you will see course greetings. This indicates that you successfully cloned my repository on your machine and pushed it over to the project host. Later on, if you ever wonder if you were able to push something over successfully, you can take a look at your repository on the project host. Those of you in the know may ask: why not just fork my repsitory? The answer: because Github won't allow you to fork a public repository into a private repository.

I'd like to take a peek at your repository, but I can't! Indeed, nobody but you can see it (hence the term private). You need to add me as a collaborator to your private repository so I can see all the hard work that you're up to. Bitbucket users: click the gear icon (**Administration**), select **Access management**, enter `lawrancej` under Users, select **Admin**, and click Add. Github users: click the wrench and screwdriver icon (**Settings**, not **Account Settings**), click **Collaborators**, enter `lawrancej`, and click Add.

Now that I can see you, why don't you watch my repository, so you know whenever I make updates? I make updates frequently, and I won't email you when I make changes. On [Bitbucket](https://bitbucket.org/lawrancej/comp278) or [Github](https://github.com/lawrancej/COMP278), click on the eye icon to watch my repository.

At this point, your local and remote repsitories are set up! Hooray!

We just need to ensure that you can commit work to wrap up this lab.

Back in the command prompt, type in the following:

	git status

Assuming you haven't messed around with your folder, you should see:

	nothing to commit, working directory clean

This means that there are no changes to the current directory as far as Git is concerned. Now let's make some changes. Type in the following command to create a new file called `test.txt` if it doesn't already exist.

	touch test.txt

Type in `git status` again. Now you will see `test.txt` listed under `Untracked files`. This means that `test.txt` is not yet in version control. Let Git track this file. Type in the following to stage it for the next commit.

	git add test.txt

Type in `git status` again. Notice that `test.txt` is now listed under `Changes to be committed`. We haven't yet recorded our change. We've only added `test.txt` to a staging area that will be part of the next commit. Don't commit just yet. Let's open up `test.txt` in a text editor. Open it up using the following command:

	start test.txt      # Windows
	open test.txt       # Mac
	gnome-open test.txt # Linux

Type in a sentence about yourself in the text editor and save it. Back in the command prompt, type in `git status` again. You will notice that `test.txt` is listed under `Changes to be committed` as well as under `Changes not staged for commit`. To see the changes not staged for commit, type in `git diff`. You will see the sentence you just typed in.

Type in the following:

	git commit -m "Added test.txt to version control."

Type in `git status` again. You will notice that the `Changes to be committed` category disappeared, because the contents of the staging area moved to the commit we just made. However, there are still changes not staged for commit. Even though we did a commit, until we stage it (add it), it won't appear as part of a commit. We could do `git add test.txt` again, but there's a shortcut. Type in the following:

	git commit -am "Added a sentence about myself."

Notice the `-am`. This adds changes to any tracked file to the commit. If we want to track an untracked file (i.e., tell Git that changes to a file are worth tracking), we still need to do `git add`.

If you look at your repository on the project host you chose, you won't see the commits there just yet. Just because you recorded a change doesn't mean it's posted online. To post your changes to your remote repository, type in the following:

	git push --all origin

This is the command you will use whenever you are ready to submit your work or work in progress.

And with that, you just completed lab 0. Booyah!

By the way, I will post new material frequently. Pull (fetch and merge) to receive updates.

	git pull origin master

Occasionally, this command won't work because we made conflicting changes. To fix a merge conflict, look for conflict markers and revise as necessary. This command makes it easier:

	git mergetool

If you want to keep only my changes, checkout their version.

	git checkout --theirs some.file.goes.here

If you want to keep only your changes, checkout our version.

	git checkout --ours some.file.goes.here

If you are thoroughly confused, examine the complete history to see what's going on.

	gitk --all &

**Note:** Even though you have removed conflict markers, you must still add files to git and commit as usual to resolve the merge conflict.

# References

* [Atlassian Git Tutorials](http://www.atlassian.com/git/)
* [Pro Git](http://git-scm.com/book)
* [Git Reference](http://gitref.org/)
* [Git Immersion](http://gitimmersion.com/)
* [Try Git](http://try.github.com/)
* [Git Branching](http://pcottle.github.io/learnGitBranching/?demo)