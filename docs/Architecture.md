# Architecture

![Image title](https://i.ibb.co/yQd7Dqg/462555434-1075664396787044-1174113531972213167-n.png){ width="800" }

This CI/CD architecture uses GitHub, TeamCity, and automated deployment to streamline the development and deployment of a web app. Developers push changes to the dev branch, which are then reviewed and merged into the main branch. TeamCity will then do a build process, running a series of build steps to ensure functionality of the project. Once successful, the application will be deployed and exposed via load balancer for users to access.

<br>
<br>
<br>


# Workflow

![Image title](https://i.ibb.co/NFKnnhv/462540541-1428153228572415-2494510043189324750-n.png){ width="800" }

This diagram outlines an iterative process for building and deploying a web application using CI/CD. It begins with the Start phase, where planning, meetings, and requirements are finalized. The Set Up phase focuses on preparing prerequisites and learning necessary technologies. Next, the Create phase involves designing the web app and configuring the CI/CD build steps. The Build phase compiles, tests, and prepares the app for deployment. In the Testing phase, unit testing is conducted to ensure code quality before deployment. Finally, the Deploy phase rolls out the latest version of the app to the live environment