# Project Requirements

## The following key tasks are necessary for the successful deployment of the web application using TeamCity:

### Web App Deployment

- **Web app requirements**
    - The web app displays a plain colored background when accessed.
    - The web app must be accessible over the internet.
    - The web-based source code (e.g., Flask or Java) must be able to be built and compiled in TeamCity.
    
- **K8s requirements**
    - The app must be set to be deployed using canary deployment strategy.
    - For every deployment, the app must always be running five (5) healthy replicas.

### TeamCity as CI/CD

- **Deploy TeamCity in your system to be used for CI/CD purposes**
    - The Git repository containing the source code of the web app must be integrated with TeamCity.
    - An automated unit test must be created.
    - Automate deployment of the web app on the K8s cluster using TeamCity.

### Version Control

- **The Git repo must have two branches that correspond to an environment:**
    - `main/master` – production environment, main source of your CI/CD pipeline.
    - `dev` – development environment, contains fixes and/or features, to be merged to `main/master` branch as necessary.

- **Branch protection must be implemented in the `main/master` branch:**
    - PRs must have an approval before getting merged.
    - A status check must be implemented and must all be passing before a PR becomes available for merging.
        - Status check requirement: the build in TeamCity must be successful.

- The GitHub repository must be used as the main storage of all info for the project: from the automation codebase, infrastructure configurations, up to project documentation.

- To show that pull request was strictly practiced, the branches’ commit history must only consist of merged pull requests.

### Ops Simulation

- **Introduce failures in your system based on (but not limited to) the following:**
    - **CI/CD failures:**
        - A breaking code change in the web app should be introduced to test if your automated unit tests are working:
            - syntax errors, or
            - logical errors such as checking if the background color of the web app was an invalid hex value.
        - A breaking config change in TeamCity should be introduced.
        - Apply the fix in Git/TeamCity in the code or config.
    - **Version control failures:**
        - Introduce a merge conflict by having different versions of a certain file on the two (2) branches – as if two people have changed the same lines in the file.
            - Show how to resolve the merge conflict, and
            - Merge the resolved conflict into `main` branch, then build and deploy the app.

- **Create respective runbooks that address each failure above.**
