# :arrow_down_small: Get the code

## In GitHub

1. [Create a new repository from this template repository](https://github.com/MikeNwin/code-to-cloud/generate) [*](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) or [duplicate this repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository).

# :white_check_mark: Test the code

## In GitHub

### Create the action

1. Go to the **Actions** tab.

2. Click on the **Set up this workflow** button of the **Node.js** workflow.

3. Click on the **Start commit** button.

4. Click on the **Commit new file** button.

### Edit a file to trigger the action

1. Go to the **Code** tab.

2. Go to the [`https://github.com/YOUR-REPOSITORY/blob/master/api/controllers/arithmeticController.js`](/api/controllers/arithmeticController.js) file.

3. Edit the file (click on the  `✎` pencil icon in the top-right corner of the file).

4. Change [`line 14`](../../edit/master/api/controllers/arithmeticController.js#L14):

   1. from `'add':      function(a,b) { return +a + +b },`

   2. to `'add':      function(a,b) { return a + b },`

5. Add a commit message (e.g. `Fix addition operation`).

6. Select "Create a **new branch** for this commit and start a pull request."

   1. Name your branch (e.g. `fix-addition-operation`)
   
7. Click on the **Propose file change** button.

### Open a pull request

1. Click on the **Create pull request** button.

2. Notice the **Node.js CI / build** failing checks.

3. Click on the **Details** on one of the failing checks.

### Explore the action output

1. Expand the failing `Run npm test` step (click on the ► right arrow character):

   1. Notice the failing `Addition` checks starting at `line 21`

# :package: Package the code

## In GitHub

### Update the references

1. Edit the `package.json` file:

   1. Change the GitHub organization or username, and repository references, to your values--e.g.:
   
      1. from `"name": "@MikeNwin/code-to-cloud"` 
      
      2. to `"name": "@YOUR-USERNAME/YOUR-REPOSITORY-NAME"`
      
      3. from `https://github.com/MikeNwin/code-to-cloud` 
      
      4. to `https://github.com/YOUR-USERNAME/YOUR-REPOSITORY-NAME`

2. Edit the `.npmrc` file:

   1. Change the GitHub organization or username to your organization or username--e.g.:
   
      1. from `@MikeNwin:registry=https://npm.pkg.github.com/`
      
      2. to `@YOUR-USERNAME:registry=https://npm.pkg.github.com/`

### Create the action

1. Go to the **Actions** tab.

2. Click on the **New workflow** button.

3. Click on the **Set up this workflow** button of the **Node.js Package** workflow.
 
4. Configure the action to publish a package to the [GitHub Package Registry](https://github.com/features/packages) (GPR):

   1. Replace `@your-github-username` with your GitHub username on line 41 (e.g. @MikeNwin).

   2. Notice `${{secrets.GITHUB_TOKEN}}` is automatically available and configured by default on line 45.

   3. Remove the `publish-npm` job at lines 18-30.

5. Click on the **Start commit** button.

6. Click on the **Commit new file** button.

### Create a release to trigger the action

1. Go to the **releases** page.

2. Click on the **Create a new release** button.

3. Enter a tag version (e.g. `v1.0`).

4. Click on the **Publish release** button.

### Explore the action output

1. Go to the **Actions** tab.

2. Notice the **Node.js Package** action is now running.

3. Wait for the **Node.js Package** action to complete.

4. Go to the **packages** page.

5. Notice a package has been published by the **Node.js Package** action.

# :rocket: Deploy the code

## In Azure

### Create the app service

1. Click on **Create a resource**.

2. Click on **Web App**.

3. Select a **Subscription** (e.g. `Visual Studio Subscription`).

4. Create a **Resource Group** or select an existing one.

5. Name the web app (e.g. `calculator`).

6. Select `Code` to **Publish**.

7. Select `Node 12` as the **Runtime stack**.

8. Select a Region (e.g. `Canada East`).

9. Create a app service plan or select an existing one (e.g. Free F1).

10. Click **Review + create**.

11. Click **Create**.

### View the new app service web site

1. Go to the newly created app service home page.

2. Click on the app service URL (e.g. `https://calculator.azurewebsites.net`).

3. Notice the app service web site is up and running—but bare and showing only a default app service landing page.

### Get the publish profile

1. Go to the app service home page.

2. Click on **Get publish profile** to download the `code-to-cloud.PublishSettings` file.

3. Open the `code-to-cloud.PublishSettings` file.

4. Copy the contents of the `code-to-cloud.PublishSettings` file.

## In GitHub

### Add the publish profile as a secret

1. Go to the **Settings** tab.

2. Go to the **Secrets** page.

3. Click on the **Add a new secret** option.

4. Name the secret `AZURE_WEBAPP_PUBLISH_PROFILE`.

5. Paste the copied contents from the `code-to-cloud.PublishSettings` file into **Value** field.

6. Click **Add secret**.

### Create the action

1. Go to the **Actions** tab.

2. Click on the **New workflow** button.

3. Click on the **Set up this workflow** button of the **Deploy Node.js to Azure Web App** workflow.

4. Configure the action to deploy to Azure:

   1. Replace `your-app-name` with your app service name created above on line 17 (e.g. `calculator`).

   2. Replace `10.x` with `12.x` on line 19.

   3. Notice `publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }}` is configured by default to consume the secret created above on line 42.
   
5. Click on the **Start commit** button.

6. Click on the **Commit new file** button.

### Explore the action output

1. Go to the **Actions** tab.

2. Notice the **.github/workflows/azure.yml** action is now running.

3. Wait for the **.github/workflows/azure.yml** action to complete.

4. Refresh the app service URL opened above (e.g. `https://calculator.azurewebsites.net`).

5. Notice the app service web site is now a functional calculator app.

# :warning: Secure the code

## In GitHub

### Enable security alerts

1. Go to the **Settings** tab.

2. Scroll down to the **Data services** section.

3. Check all the boxes for the options:

   1. **Allow GitHub to perform read-only analysis of this repository**
   
      1. **Dependency graph**
      
      2. **Security alerts**

### View security alerts

1. Go back to the **Code** tab.

2. Notice security alerts are enabled and a prominent banner appears.

3. Click on the **View security alerts** button.

4. Notice the open security alerts of varying severity.

5. Notice a pull request is automatically opened for **lodash**.

### View security updates

1. Click on the pull request automatically opened for **lodash**.

2. Notice **dependabot** has automatically opened a pull request to update the security vulnerabilities.

3. Click on the Commits details in the first comment of the pull request to view the changes made by dependabot.

4. Merge the pull request.
