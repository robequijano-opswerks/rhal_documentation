# Solutions

!!! Warning "Limitations"

    - Direct pushes or commits to the main branch of the GitHub repository are not allowed. Only pull requests (PRs) are permitted, requiring review and approval before merging.
    - Git branch protection cannot be enforced due to restrictions on the private repository.
    - Only color names must be input in the environment variable; hex codes and empty values are not allowed.

Using TeamCity, the developers have set up a CI/CD system that handles the following:

### A. Web App Deployment
- The web application successfully displays a plain colored background when accessed using hex color codes.
- The web application is exposed using a load balancer and is accessible over the internet.
- The web application is built using Flask and compiled in TeamCity.
- The web application is deployed using a canary deployment strategy.

### B. Version Control Management/Code Management
- Using Git/GitHub to track the updates and changes of the project. It has two branches: `main` and `dev`.
  
- Branch protection was not enforced due to the repository being private. **Solution:** The developers were able to practice branch protection by cloning the repository to a public repository and then implemented the branch protection.

- All changes were submitted through Pull Requests and were approved before being merged.

- The GitHub repository served as the main storage for all data related to the project.

### C. TeamCity as CI/CD (Auto-Testing)
- Once developers made changes to the GitHub repository, TeamCity will automatically run unit tests and rebuild the project. This ensures that the changes made to the project will work well and won't continue upon failure.

### D. Deployment
- When all tests pass, TeamCity will now be able to automatically deploy the project to the live environment. The web application will now be accessible to the users.

---

## Tools

| Method         | Description                          |
| -------------- | ------------------------------------ |
| `Pytest`       | a tool to write and run tests. 
| `Flask`        | a python web framework for building web applications and APIs.
| `TeamCity`     | a CI/CD server used for automating processes like building, testing, and deploying applications
| `Github`       | tool used for version control management and collaborative purposes
| `Webcolor`     | tool to covert color names to hex codes
| `Werkzeug`     | a component of Flask used as a toolkit for building web applications. 
| `Docker`       | used to build, push and pull images. Also used for containerization of application
| `Kubernetes`   | used for automation of deployments, scaling, and management.
| `Java/JDK17`   | (Java Development Kit) that provides tools for developing and running Java applications.
| `Homebrew`     | open-source software package management system use for installation of softwares 
| `Python`       | programming language used for web development
| `Kubectl`      | a command-line tool used to interact with Kubernetes.
| `Pip`          | Used for installing, upgrading, and manage Python  packages and libraries.

<br>

## Disaster Recovery Plan

## A. CI/CD Failure

To test if automated unit testing is working, below are scenarios that break the code and solutions to fix them:

### Syntax Error or Logical Error in GIT

If the value of the `COLOR` variable in the `.env` file is incorrect, like:

```bash
COLOR=Blueeee
```

It will result in a build failure in pytest; Shown below is the error message

``` bash
================ short test summary info =================== 
FAILED tests/test_main_server.py::test_background_color - ValueError: "Blueeee" is not defined as a named color in css3
================ 1 failed in 0.35s =========================
```

### To Fix:
Ensure that the value in the variable name is valid (a recognized CSS color name).

1. Open your `.env` file using the command:
    ```bash
    vi .env
    ```

2. Change the value:
    ```bash
    COLOR=<validColorName>
    ```

Example:
```bash
COLOR=BLUE
```

<br>
## B. Breaking Config Change in TeamCity

### Disabled a Build Step

When a build step is in a disabled status, the build won't be successful and will result in an error.

Example Error Message:

```bash
Step 3/4: Push (Docker) < 1s
Starting: /bin/sh -c docker push eywrld839/webapp:dev && docker push eywrld839/webapp:20 in directory: /Users/academy/Downloads/TeamCity/buildAgent/work/40d27028a6259cf2
The push refers to repository [docker.io/eywrld839/webapp]
tag does not exist: eywrld839/webapp:dev
Process exited with code 1
Process exited with code 1 (Step: Push (Docker))
Removing pushed images/tags from build agent: eywrld839/webapp:dev eywrld839/webapp:20
Step Push (Docker) failed
```

### To Fix:

1. Navigate to:  
   **Projects** > **(Project Name)** > **Build Configuration** > **Edit Configuration** > **Build Steps**.
   
2. Click the dropdown button of the disabled build step, then select **Enable Build Step**.

<br>

## C. Merge Conflicts

Merge conflicts occur whenever a file/data is manipulated or modified from two different branches or sets of changes.

In the example below, we introduce a merge conflict error by changing the value within the `.env` file at the same time and on the same line.

=== "First POV"

    ```bash
    vi .env
    COLOR=White
    ```

=== "Second POV"

    ```bash
    vi .env
    COLOR=Yellow
    ```
<br>

After **GIT PUSH**, You will encounter git merge conflict since the same file was editted at the same time without pulling first

```bash
Auto-merging .env
CONFLICT (content): Merge conflict in .env
Automatic merge failed; fix conflicts and then commit the result.
academy@Academy16s-MacBook-Pro devwebapp % git status
On branch dev
Your branch and 'origin/dev' have diverged,
and have 1 and 1 different commits each, respectively.
(use "git pull" if you want to integrate the remote branch with yours)

You have unmerged paths.
(fix conflicts and run "git commit")
(use "git merge --abort" to abort the merge)

Unmerged paths:
(use "git add <file>..." to mark resolution)

both modified:   .env
```
### To Fix:

1. Retrieve the latest changes from the remote repository without merging them into your current branch:
    ```bash
    git fetch origin
    ```
    * This will retrieve the latest changes but won’t automatically merge them into your current branch.

2. Merge the latest changes from the remote `dev` branch into your local branch:
    ```bash
    git merge origin dev
    ```
    * This will merge the latest changes from the `dev` branch into your local branch.

This process will show you the file that has a merge conflict.

### To Resolve the Merge Conflict:

1. Open the `.env` file:
    ```bash
    vi .env
    ```
   This will show the data that needs to be changed/corrected:
    ```bash
    <<<<<<< HEAD
    COLOR=White
    =======
    COLOR=Yellow
    >>>>>>> origin/dev
    ```

2. Save the changes and add the file to the staging area:
    ```bash
    git add .env
    ```

3. Commit the changes:
    ```bash
    git commit -m "Resolved merge conflict for .env file"
    ```

4. Push to the dev repository:
    ```bash
    git push origin dev
    ```

### To Merge Changes from Dev to Main:

1. **Create a Pull Request** from `dev` to `main`.
   - Specify the description of the change: **"Change Background color to Yellow"**.

2. **Add a reviewer** to check your pull request, then wait for approval.

3. Once approved and merged:
   - With the updated `main` branch in GitHub, TeamCity will now rebuild and deploy the new web application with the specified background color.
