# Solutions

## Using TeamCity, the developers have set up a CI/CD system that handles the following:

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

# Tools

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