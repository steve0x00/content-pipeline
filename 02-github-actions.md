GitHub Actions
===

Examine the GitHub Pages workflow
---
GitHub can automatically process the files in your repository when
certain events occur. For example, when the content of a branch
is updated, or when a branch is merged into another one. 

This feature is called GitHub Actions, and it drives GitHub Pages.
Take a closer look in your repository:

1. On your main repository page, find **Deployments** in the lower-right
   corner. You'll see badge telling you how many times a workflow resulted
   in deploying artifacts to a destination.

   You have some runs of `github-pages`, which deployed HTML and CSS to 
   your GitHub pages site. This was the result of a workflow.

   > **Note:** The name of this product is GitHub Actions, but it should
   > be called GitHub Workflows. Workflows define a series of steps that
   > GitHub can perform on your content, some of which *might* include
   > "actions."

1. Click **Actions** in the top navigation.

   On the left side, under **Workflows**, you'll see `pages-build-deployment`.

   In the middle of the page you'll see each run of that workflow. 

1. Click a workflow run to see its details. 

   This workflow has three jobs, `build`, `report-build-status`, and `deploy`.

1. Click the `build` job. This shows individual steps comprising the job.

   Expand some of the steps and log lines to see the work it did. It's a lot!

Extend the workflow
--

### Make the GitHub Pages workflow modifiable
It would be useful if content were automatically spell-checked before 
being deployed to your GitHub Pages. You would need to modify the workflow
file to do this.

The `pages-build-deployment` workflow is maintained by GitHub. You can't 
view its code or modify it. But you can create your own workflow that 
does the same thing and more.

1. On the **Actions** page on the left hand side, click **New Workflow**

1. Notice the many workflows available!

   Scroll down to the **Pages** section and locate the **GitHub Pages Jekyll** card. 
   This is the template that the default GitHub Pages workflow uses. 

   Click **Configure**. This will open the workflow file in the basic editor.

1. Examine the workflow YAML file. Notice under `jobs` there are `build`  and
   `deploy`, just like the jobs you saw in the workflow run logs.

   Also notice the filepath. Github workflows are always located a the root of
   your repository in the directory `.github/workflows/`. 

1. Click **Commit changes...**, and then **Commit changes**.

1. Click **Actions**. 

   Notice that there is now **Deploy Jekyll with GitHub Pages dependencies** available.

1. Click the new workflow and then click **Run workflow** on the right-hand side.

   Click the second **Run workflow** button

   In a moment, the run will appear in the list with an orange indicator. It will turn
   green when the deployment is complete.

Currently, the original workflow will still run when new commits are made to `main`,
and your new workflow will only run when manually triggered. Next, you will update
your GitHub Pages configuration to automatically run only new workflow.

1. Click on **Settings** in the top navigation bar. Then click on **Pages**.

1. Under **Build and deployment**, set **Source** to GitHub Actions.

   Notice that it gives you the option to configure **GitHub Pages Jekyll** from 
   here, too. GitHub will realize you have already done this after your next
   deployment.

### Test the new workflow

1. Either create a new file in your repository or edit one of the existing ones
   such as `README.md` or `index.md`.  When you commit the changes, you should
   see the new workflow start.

1. When the new workflow is complete, view your GitHub Pages site and confirm
   that the change you made have been deployed.

Add a new action to the workflow
---
Now that you have a modifiable workflow that is deploying your GitHub pages
correctly, you can extend it to add an action to spell check Markdown files
beore deploying them. If it catches any errors, it will break the build and
the error won't be pushed.

1. Go to the [GitHub Actions Marketplace](https://github.com/marketplace)
   and search for `spelling`.

1. Click **typos-action**.

1. Under **Documentation**, click **GitHub Action**.

   You will see a workflow file that uses this action in several steps. 

1. Copy the second step, named `Check spelling of file.txt`:

   ```
   - name: Check spelling of file.txt
     uses: crate-ci/typos@master
     with: 
       files: ./file.txt
   ```

1. Return to your GitHub repository and and click the **Code** tab in the 
   global navigation bar. 

1. Open the file `.github/workflows/jekyll-gh-pages.yml` and click the
   **pencil icon** to edit it.

1. In the `build` job, paste the `Check spelling of file.txt` step that
   you copied between the `Checkout` step and `Setup Pages` step. 

1. Update the pasted step to only spell check `*.md` files:

   ```
   - name: Check spelling of Markdown files
     uses: crate-ci/typos@master
     with: 
       files: '**/*.md'
   ```
1. Commit your changes with the message `Add spell checking action`.

   This will automatically start the workflow.

1. Click the **Actions** tab in the navigation tab to see the progress of the
   workflow.

   After a minute or so, the workflow will either succeed and deploy if it
   finds no typos, or it will fail.  

   If it fails, you'll notice that the `deploy` job didn't run.

   Correct the typos in the indicated files and commit the changes. It should
   pass and deploy on the next build.

===

Examine the GitHub Pages workflow
---
GitHub can automatically process the files in your repository when
certain events occur. For example, when the content of a branch
is updated, or when a branch is merged into another one. 

This feature is called GitHub Actions, and it drives GitHub Pages.
Take a closer look in your repository:

1. On your main repository page, find **Deployments** in the lower-right
   corner. You'll see badge telling you how many times a workflow resulted
   in deploying artifacts to a destination.

   You have some runs of `github-pages`, which deployed HTML and CSS to 
   your GitHub pages site. This was the result of a workflow.

   > **Note:** The name of this product is GitHub Actions, but it should
   > be called GitHub Workflows. Workflows define a series of steps that
   > GitHub can perform on your content, some of which *might* include
   > "actions."

1. Click **Actions** in the top navigation.

   On the left side, under **Workflows**, you'll see `pages-build-deployment`.

   In the middle of the page you'll see each run of that workflow. 

1. Click a workflow run to see its details. 

   This workflow has three jobs, `build`, `report-build-status`, and `deploy`.

1. Click the `build` job. This shows individual steps comprising the job.

   Expand some of the steps and log lines to see the work it did. It's a lot!

Extend the workflow
--

### Make the GitHub Pages workflow modifiable
It would be useful if content were automatically spell-checked before 
being deployed to your GitHub Pages. You would need to modify the workflow
file to do this.

The `pages-build-deployment` workflow is maintained by GitHub. You can't 
view its code or modify it. But you can create your own workflow that 
does the same thing and more.

1. On the **Actions** page on the left hand side, click **New Workflow**

1. Notice the many workflows available!

   Scroll down to the **Pages** section and locate the **GitHub Pages Jekyll** card. 
   This is the template that the default GitHub Pages workflow uses. 

   Click **Configure**. This will open the workflow file in the basic editor.

1. Examine the workflow YAML file. Notice under `jobs` there are `build`  and
   `deploy`, just like the jobs you saw in the workflow run logs.

   Also notice the filepath. Github workflows are always located a the root of
   your repository in the directory `.github/workflows/`. 

1. Click **Commit changes...**, and then **Commit changes**.

1. Click **Actions**. 

   Notice that there is now **Deploy Jekyll with GitHub Pages dependencies** available.

1. Click the new workflow and then click **Run workflow** on the right-hand side.

   Click the second **Run workflow** button

   In a moment, the run will appear in the list with an orange indicator. It will turn
   green when the deployment is complete.

Currently, the original workflow will still run when new commits are made to `main`,
and your new workflow will only run when manually triggered. Next, you will update
your GitHub Pages configuration to automatically run only new workflow.

1. Click on **Settings** in the top navigation bar. Then click on **Pages**.

1. Under **Build and deployment**, set **Source** to GitHub Actions.

   Notice that it gives you the option to configure **GitHub Pages Jekyll** from 
   here, too. GitHub will realize you have already done this after your next
   deployment.

### Test the new workflow

1. Either create a new file in your repository or edit one of the existing ones
   such as `README.md` or `index.md`.  When you commit the changes, you should
   see the new workflow start.

1. When the new workflow is complete, view your GitHub Pages site and confirm
   that the change you made have been deployed.

Add a new action to the workflow
---
Now that you have a modifiable workflow that is deploying your GitHub pages
correctly, you can extend it to add an action to spell check Markdown files
beore deploying them. If it catches any errors, it will break the build and
the error won't be pushed.

1. Go to the [GitHub Actions Marketplace](https://github.com/marketplace)
   and search for `spelling`.

1. Click **typos-action**.

1. Under **Documentation**, click **GitHub Action**.

   You will see a workflow file that uses this action in several steps. 

1. Copy the second step, named `Check spelling of file.txt`:

   ```
   - name: Check spelling of file.txt
     uses: crate-ci/typos@master
     with: 
       files: ./file.txt
   ```

1. Return to your GitHub repository and and click the **Code** tab in the 
   global navigation bar. 

1. Open the file `.github/workflows/jekyll-gh-pages.yml` and click the
   **pencil icon** to edit it.

1. In the `build` job, paste the `Check spelling of file.txt` step that
   you copied between the `Checkout` step and `Setup Pages` step. 

1. Update the pasted step to only spell check `*.md` files:

   ```
   - name: Check spelling of Markdown files
     uses: crate-ci/typos@master
     with: 
       files: '**/*.md'
   ```
1. Commit your changes with the message `Add spell checking action`.

   This will automatically start the workflow.

1. Click the **Actions** tab in the navigation tab to see the progress of the
   workflow.

   After a minute or so, the workflow will either succeed and deploy if it
   finds no typos, or it will fail.  

   If it fails, you'll notice that the `deploy` job didn't run.

   Correct the typos in the indicated files and commit the changes. It should
   pass and deploy on the next build.

The next page provides a [list of useful Actions](./03-more-resources.md) to illustrate some of the
ways you can extend and enhance any workflow.
