# cs1302-ce29 Complexity Classes

![Approved for: Fall 2019](https://img.shields.io/badge/Approved%20for-Fall%202019-brightgreen)
<!--![Approved for: Spring 2020](https://img.shields.io/badge/Approved%20for-Spring%202020-blue)
![Instruction: Online](https://img.shields.io/badge/Instruction-Online-important)-->

In this class exercise, you will gain a deeper understanding of the notable complexity classes by plotting 
the functions using a JavaFX `LineChart`. By the end of the exercise, your application should show all of
the notable complexity classes in the `LineChart`. The final product should look similar to the image below.

![`Final Product`](https://github.com/cs1302uga/cs1302-ce29/raw/master/Final.png)

## Course-Specific Learning Outcomes
* **LO3.d:** Apply pair-programming principles in a software-based project.
* **LO5.a:** Utilize a version control tool such as Git or Subversion to store 
and update source code in a multi-programmer software solution.
* **LO6.c:** (Partial) Implement, analyze, and assess combinations of searching/sorting 
algorithms such as linear search, binary search, quadratic sorts, and linearithmic sorts.

## References and Prerequisites

* [`CSCI 1302 Big-O Tutorial`](http://cobweb.cs.uga.edu/~mec/cs1302-bigo/)
* Java Generics
* Lambda Expressions
* A basic understanding of JavaFX and the `LineChart` class.

## Questions

In your notes, clearly answer the following questions. These instructions assume that you are 
logged into the Nike server. 

**NOTE:** If a step requires you to enter in a command, please provide in your notes the full 
command that you typed to make the related action happen. If context is necessary (e.g., the 
command depends on your present working directory), then please note that context as well.

### Getting Started
   
1. To get the most out of this exercise, we encourage you to
   **form a group of exactly two people for this exercise.**
   
   * **Working in a group?** Some steps in this exercise need be done by each group member individually.
   If a step is being performed by one group member, then everyone is expected
   to watch, pay attention, and take notes. We recommend that you use Comte de Rochambeau's technique 
   to determine who gets to be group member 1 and group member 2.
   
   * **Working by yourself?** That's okay. If the instructions ask you to switch, then don't switch.

1. **Individually:** Make sure that you have done the following:

   1. [Setup your Free GitHub Pro Account](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md#setting-up-an-account)
   
   1. [Setup your SSH Keys on Nike and GitHub](https://github.com/cs1302uga/cs1302-tutorials/blob/master/github-setup.md#setting-up-ssh-keys)

1. **Individually:** If you haven't already done this in a previous exercise, setup your Git username 
   and email on Nike by modifiying and executing the commands below. 
   When setting the `user.name` property, please provide your name as it appears on eLC and
   Athena. If you have a preferred name, then you may include it in parentheses. For the
   `user.email` property, please use your `@uga.edu` email address:

   ```
   $ git config --global user.name "Mona Lisa (Liz)"
   $ git config --global user.email "email@uga.edu"
   ```
   
   You can verify that these properties were setup correctly by observing the output of
   the following commands:
   
   ```
   $ git config --global user.name
   $ git config --global user.email
   ```
   
1. If asked, please be ready to show the public key that you generated on Nike both on
   Nike and on your GitHub account.
   
   * To see the copy of your public key on Nike:
     ```
     $ cat ~/.ssh/id_rsa.pub
     ```
   * To see the copy of your public key on GitHub, please visit: https://github.com/settings/keys
   
1. **GROUP MEMBER 1:** Create a [new repository](https://github.com/new) on GitHub with 
   the following information:
   
   Do **NOT** "Initialize this repository with a README". 
   Also, do **NOT** click on the dropdowns for a `.gitignore` or license file.
   
   | **Field**            | **Value**                                                        |
   |----------------------|------------------------------------------------------------------|
   | **Owner**            | _your account_                                                   |
   | **Repository Name**  | `cs1302-ce29`                                                    |
   | **Description**      | `Repository for Class Exercise 29`                               |
   | **Public / Private** | Private -- You choose who can see and commit to this repository. |
   
   Once complete, you should have a GitHub-hosted private Git repository at the following
   website URL: `https://github.com/your_username/cs1302-ce29` where `your_username` is
   your GitHub account username. 
   
   Do **NOT** follow any of the setup instructions given on GitHub at this time.
   
1. **If not in a group,** skip to the next step; otherwise, perform the sub-steps below.   

   1. **GROUP MEMBER 1:** On the repository's website, add your group members as collaborators
      by going to "Settings" → "Collaborators". This will send them an invite that they can
      accept either via email or by visiting the repository's website on GitHub.
   
   1. **GROUP MEMBER 2:** Go to the repository website on GitHub and accept the invition
      from Group Member 1. If you see a 404 error instead of an invitation, then double check
      the following:
   
      * Repository Website URL
   
      * Username that Group Member 1 used when they added you
   
      Before continuing, make sure each group member has access to the repository website.  
   
1. **In the remaining instructions,**
   **`TEAM_REPO_SSH` will refer to the SSH URL for that repository as provided by GitHub.**
   The SSH URL is not the same as the URL above. It should look like: 
   `git@github.com:your_username/cs1302-ce29.git` where `your_username` is
   your GitHub group member 1's username. 

1. One team member should clone their empty team repository to their Nike account and
   setup a link to the remote skeleton repository provided by your instructor. A sequence
   of commands is provided below. You should make every effort to understand what
   each command is doing *before* you execute the command.

   ```
   $ git clone TEAM_REPO_SSH cs1302-ce29
   $ cd cs1302-ce29
   $ git remote add skeleton https://github.com/cs1302uga/cs1302-ce29.git
   $ git pull skeleton master
   $ git push origin master
   ```

   This team member should now be good to go. A pair programming workflow is provided
   in the [Appendix - Workflow](#appendix---workflow) section, which provides an
   overview of one way to send / receive changes from team member to team member
   while minimizing basic merge conflicts.

1. The other team member should now be able to perform the same sequence of steps,
   omitting the last two steps:

   ```
   $ git clone TEAM_REPO_SSH cs1302-ce29
   $ cd cs1302-ce29
   $ git remote add skeleton https://github.com/cs1302uga/cs1302-ce29.git
   ```

1. Change into the `cs1302-ce29` directory that you just set up and look around. There should be
   multiple Java files contained within the directory structure. To see a listing of all of the 
   files under the `src` subdirectory, use the `find` command as follows:
   
   ```
   $ find src
   ```
   
1. You should also notice the provided `pom.xml` and `Makefile`. The `Makefile` may be used to compile 
   and run your code. However, the code will not run correctly at this time.
   
## Exercise Steps

1. While looking in the `src` directory, you likely saw a file called `ChartUtility.java`. 
   This file contains a utility class with some helpful methods for creating JavaFX line charts.
   Using the provided methods will allow you to focus on plotting the complexity class functions
   instead of the details of how to build a line chart.
   
   Take a few minutes to familiarize yourselves with the documentation for these methods 
   using the documentation found here: 
   [Chart Utility](http://cobweb.cs.uga.edu/~mec/cs1302-ce29-doc/)

1. Take a few more minutes to read through `ComplexityClasses.java`. This file contains a `start` method
   which does the following:
   * Creates a JavaFX `LineChart` and adds a data series representing a constant (`O(1)`) function using 
     the `createChart` method of `ChartUtility`.
   * Adds a series representing a linear (`O(n)`) function using the `addSeries` method of `ChartUtility`. 
   * Sets up the scene, and adds the scene to the stage. 
   
1. Pair Program:

   * **Current Pair Programming Driver (person typing)**: Open the `ComplexityClasses.java` file
     and implement the `genData` method. Read the associated Javadoc (including the example) along 
     with the example usage of `genData` in the `start` method of `ComplexityClasses` to guide 
     your implementation.
   
   * **Current Pair Programming Rider**: Stay actively engaged with your group member while
     they are working. Offer suggestions and point out typos or logical errors as they work. 
   
1. Once you complete `genData`, execute the `make` command to compile and run your code. If you 
   notice that the plots are close to the bottom of the graph, you may need to decrease the 
   `Y_FINAL` variable in `ComplexityClasses.java`. Try a few different values to get the plot
   to clearly show the plot lines.

1. After you've confirmed that the code compiles, runs, and shows a nice looking plot, add and 
   commit your changes to the local repository.

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-1-success?style=for-the-badge)

<hr/>

1. **Swap drivers.** Call the `addSeries` method of `ChartUtility` to plot the following 
   linear functions for `0 <= n <= 100`.

   * `1.0 * n + 2.0`
   * `1.2 * n + 1.0`
   * `1.4 * n - 1.0`
   * `1.6 * n`
   
   Use `make` to compile and run the code. After you've confirmed that it compiles and runs (and shows
   a nice looking plot), add and commit your changes to the local repository.
   
   **Write the answers to the following questions in your notes:** 
      1. If you increase `X_FINAL` to `500` and `Y_FINAL` to `10000`, what do you observe?
      1. If you increase `Y_FINAL` to `20000`, what do you observe?

1. Change `X_FINAL` and `Y_FINAL` back to `100`.

1. **Swap drivers.** Call the `addSeries` method of `ChartUtility` to plot the following 
   quadratic functions for `0 <= n <= 100` in addition to any previous functions plotted.

   * `Math.pow(n, 2.0) + 2.0 * n - 1.0`
   * `2.0 * Math.pow(n, 2.0) + 1.5 * n + 2.0`
   * `1.5 * Math.pow(n, 2.0) + 2.0 * n - 3.0`
   * `Math.pow(n, 2.0) + 42.0`
   
   Use `make` to compile and run the code. After you've confirmed that it compiles and runs (and shows
   a nice looking plot), add and commit your changes to the local repository.
   
   **QUESTION (answer in your notes):** As you increase `Y_FINAL`, do these functions group together or 
   separate more when compared to:
   
   * each other?
   * the linear functions?

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-2-success?style=for-the-badge)

<hr/> 

1. **Swap drivers.** Call the `addSeries` method of `ChartUtility` to plot the following 
   cubic functions for `0 <= n <= 100` in addition to any previous functions plotted.

   * `1.1 * Math.pow(n, 3.0) + 1.3 * n - 4.0`
   * `2.2 * Math.pow(n, 3.0) + 1.5 * n + 2.0`
   * `1.5 * Math.pow(n, 3.0) + n - 3.5`
   * `Math.pow(n, 3.0) - 42.0`
   
   Use `make` to compile and run the code. After you've confirmed that it compiles and runs (and shows
   a nice looking plot), add and commit your changes to the local repository.
   
   **QUESTION (answer in your notes):** As you increase `Y_FINAL`, do these functions group 
   together or separate more when compared to:
   
   * each other?
   * the quadratic functions?
   * the linear functions?
   
1. **Swap drivers.** Call the `addSeries` method of `ChartUtility` to plot the following 
   exponential functions for `0 <= n <= 100` in addition to any previous functions plotted.

   * `Math.pow(2.0, n) + Math.pow(n, 2.0)`
   * `Math.pow(1.5, n) + 32.0`
   * `Math.pow(1.3, n) + n`
   * `2.0 * Math.pow(1.2, n) - 0.5 * Math.pow(n, 3.0)`
   
   Use `make` to compile and run the code. After you've confirmed that it compiles and runs (and shows
   a nice looking plot), add and commit your changes to the local repository.
   
   **QUESTION (answer in your notes):** As you increase `Y_FINAL`, do these functions group together 
   or separate more when compared to:
   
   * each other?
   * the cubic functions?
   * the quadratic functions?
   * the linear functions?
   
1. **QUESTION (answer in your notes):** What do you think the instructors are tying to get you to see 
   with all these plots?
   
<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-3-success?style=for-the-badge)

<hr/>

### Submission Steps

**Each student needs to individually submit their own work.**

1. Create a plain text file called `SUBMISSION.md` directly inside this exercise
   directory with the following information:

   1. Your name and UGA ID number;
   1. Collaborator names, if any; and
   1. The weekly code (listed with the exercise on eLC).
   
   Here is an example:
   
   ```
   1. Sally Smith (811-000-999)
   2. Collaborators: Joe Allen, Stacie Mack
   3. Weekly Code: replace-with-actual-code
   ```

1. Add and commit `SUBMISSION.md`. Also, do a final check to ensure your code 
   passes the `checkstyle` audit, then stage and commit all changes.

1. Change into the parent directory and use the `submit` command to submit this exercise to `cs1302a`:
   
   ```
   $ submit cs1302-ce29 cs1302a
   ```
     
<hr/>

![CP](https://img.shields.io/badge/Just%20Finished-Submission-success?style=for-the-badge)

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
