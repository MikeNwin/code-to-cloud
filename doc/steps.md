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

4. Expand the failing `Run npm test` step (click on the ► right arrow character):

   1. Notice the failing `Addition` checks starting at [`line 21`](../../runs/424494825?check_suite_focus=true#step:6:21)

# :package: Package the code

## In GitHub

### Update the references

1. Edit the `package.json` file:

   1. Change the GitHub organization or username, and repository references to your values--e.g.:
   
      1. from `"name": "@MikeNwin/code-to-cloud"` 
      
      2. to `"name": "@YOUR-USERNAME/YOUR-REPOSITORY-NAME"`
      
      3. from `https://github.com/MikeNwin/code-to-cloud` 
      
      4. to `https://github.com/YOUR-USERNAME/YOUR-REPOSITORY-NAME`

### Create the action

1. Go to the **Actions** tab.

2. Click on the **New workflow** button.

3. Click on the **Set up this workflow** button of the **Node.js Package** workflow.

4. Configure the action:

   1. Remove the `publish-npm` job (i.e. lines 18-30).
   
   2. Add your GitHub username to the `scope` of the `publish-gpr`.
   
   3. Notice `${{secrets.GITHUB_TOKEN}}` is available and configured by default.
   
5. Click on the **Start commit** button.

6. Click on the **Commit new file** button.
