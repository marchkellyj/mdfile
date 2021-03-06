<!--
 * @Author: your name
 * @Date: 2020-07-27 23:06:35
 * @LastEditTime: 2020-07-28 00:29:35
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedc:\Users\Mark\Desktop\md\maintain.md
--> 
# Maintain Capstone 2020 Solution App


# Introduction

* In this tutorial, I'll show you how to maintain Capstone 2020 solution app.
* Instead of using OpenShift and the local environment, using [Netlify](https://www.netlify.com/) as the example of a platform for hosting/maintaining our solution app.

## How to Taking Control the Solution Code from Gov's master Repository to Your Repository

1. Navigate into our [solution repository](https://github.com/bcgov/CITZ-IMB-Capstone2020)


2. Create a fork for the solution app by clicking the "Fork" button in the upper right corner<br />

    ![Screenshot](./images/Fork.png)

3. Download the forked solution app in your local by following [build.md](./build.md)


4. (**Optional**) If you have Contributors, you also have to make the connection between your local and the master branch for the solution app. You have to check out is your local up-to-date with master branch or not before you wants to make a pull request. If you don't do so yu might over-write others work.

   * Checkout your remote url, run following command in terminal:
   ```sh
   $ git remote -v
    origin  https://github.com/Murphy316/CITZ-IMB-Capstone2020 (fetch)
    origin  https://github.com/Murphy316/CITZ-IMB-Capstone2020 (push)
   ```

   * Adding a upstream url, run following command in terminal:
   ```sh
   $ git remote add upstream https://github.com/bcgov/CITZ-IMB-Capstone2020.git
   ```
   * Checkout your remote url again, run following command in terminal:
   ```sh
   $ git remote -v
    origin  https://github.com/Murphy316/CITZ-IMB-Capstone2020 (fetch)
    origin  https://github.com/Murphy316/CITZ-IMB-Capstone2020 (push)
    upstream        https://github.com/bcgov/CITZ-IMB-Capstone2020.git (fetch)
    upstream        https://github.com/bcgov/CITZ-IMB-Capstone2020.git (push)
   ```
   * To upstream your local solution code, run following command in terminal:
   ```sh
   $ git pull upstream master
    remote: Enumerating objects: 1, done.
    remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 1
    Unpacking objects: 100% (1/1), done.
    From https://github.com/bcgov/CITZ-IMB-Capstone2020
    * branch            master     -> FETCH_HEAD
    * [new branch]      master     -> upstream/master
    Already up to date!
   ```
5. Add you change, commit your change, and push your change to your forked repository by running:
   ```sh
   $ git add .
   $ git commit -m "initial commit"
   $ git push
   ```
## How to Make a Pull Request From Your Forked Repository to Master Repository 

1. Compared with your forked repository, if the master repository is not update-to-date, your **forked repository** will look like following here. Click "Pull Request" to create a pull request from your forked repository to master 

    ![Screenshot](./images/pull.png)<br />

2. Click create new pull request<br />

    ![Screenshot](./images/pull2.png)

3. (**Until here is everything you have to do**)Add at least one reviewer<br />

    ![Screenshot](./images/reviewers.png)

4. Wait at least one admin reviewed your changes, until [pipeline finish deployment](./deploy.md), and finally admin will click "merge" button

## How to deploy your local solution app to [Netlify](https://www.netlify.com/) for testing

### <ins>NOTICE</ins>: You can create a new project in Netlify directly use the solution repo in GitHub (by using webhooks); However, GitHub will keep throwing some security notification if your account has 2-factor authentication

1. Navigate to [Netlify](https://www.netlify.com/)

2. Login with Github/ GitLab/ Bitbucket/ Email

3. Assume your solution code works fine locally <br/>
   Testing by run following command in terminal:
   ```sh
   $ npm start
   ```

4. Run following command in your solution root folder (the folder has package.json).. This command will generate a ./build folder under the root folder. The build folder has everything for deploying the product.
   ```sh
   $ npm run build
    > capstone2020@0.10.1 build E:\demo\CITZ-IMB-Capstone2020
    > react-scripts build

    Creating an optimized production build...
    Compiled successfully.

    File sizes after gzip:

    87.44 KB  build\static\js\2.31a99ac9.chunk.js
    22.47 KB  build\static\css\2.af3c1da9.chunk.css
    5.33 KB   build\static\js\main.414fb813.chunk.js
    850 B     build\static\css\main.aab31845.chunk.css
    777 B     build\static\js\runtime-main.9d16b1e1.js

    The project was built assuming it is hosted at /.
    You can control this with the homepage field in your package.json.

    The build folder is ready to be deployed.
    You may serve it with a static server:

    serve -s build

    Find out more about deployment here:

    bit.ly/CRA-deploy

   ```
   <br/>

   ![Screenshot](./images/folder.png)

5. Click “Sites” in Netlify.

    ![Screenshot](./images/drag.jpg)

6. Drag ./build folder into the bottom of the “Sites” page. Netlify will automatically navigate to the project overview page after drag action.<br/>

    ![Screenshot](./images/drag.png)

7. The overview page will pop-up after deployment. Open the solution app by clicking the URL under the overview page.

    ![Screenshot](./images/app.png)