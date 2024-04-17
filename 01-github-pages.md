Set up GitHub Pages
===
GitHub Pages is a feature of GitHub that will automatically create
a web site from the contents of your repository.

Create the repository
---
1. Log in to your [GitHub](https://github.com) account

1. Go to your GitHub account main page.

1. Click the **plus icon** in the upper-right corner.  Select `New repository`.

1. In the **Repository name** field, enter the following
   ```
   content-pipeline
   ```

1. Leave **Public** selected.

1. Under **Initialize this repository with:**, check **Add a README file**.

1. Click **Create repository** in the lower-right corner.

Update the README
---
1. Click the `README.md` file to open it in the basic editor.

1. In the upper-right corner, click the **pencil icon** to edit the file.

1. Select **Edit in place**.

1. Paste the following into `README.md`:
   ```
   README
   ===
   This is a proof of concept of a content delivery pipeline. It uses
   [GitHub Pages](https://pages.github.com)
 
   ![The GitHub Pages logo](https://pages.github.com/images/logo.svg)
   ```

1. Click **Commit Changes...** in the upper-right corner.

1. In the **Commit message** field, paste the following:
   ```
   Initial content for the README file
   ```

1. Click **Commit changes**

Enable GitHub Pages functionality
---
1. In the top menu bar, click **Settings**. In the left hand menu, click **Pages** 

1. Under **Branch**, click **None** and select select `main`

1. Click **Save**

1. The URL of your GitHub Pages site will be in the form `https://<username>.github.io/content-pipeline`

1. In a new browser tab or window, navigate to this URL in your browser. 

   You'll see the `README.md` file rendered as the homepage. GitHub pages looks
   for one of the following files to render, in order of preference: `index.html`,
   `index.md`, `README.md`

   A README is typically used for repository documentation. For you content,
   create a new `index.md` file

Create a new homepage
---
1. Return to you repository and click **Code** in the top navigation bar

1. Click **Add file** and select **+ Create new file**

1. In the **Name your file...** field, enter `index.md`

1. In the **Enter file contents here** field, enter your content. For example:
   ```
   Building a Content Delivery Pipeline
   ===
   Welcome! This site will walk you through creating an automated workflow
   for publishing content to GitHub Pages. All you need is a web browser!
   ```

1. Click **Commit changes...**. 

   In the **Commit message** field, paste the following:

   ```
   Created site homepage.
   ```

1. Click **Commit changes** and refresh your GitHub Pages site. You'll see that
   `README.md` has been replaced with `index.md`

In the [next activity](./02-github-actions.md), you'll automate spell-checking your content by adding
a GitHub Actions workflow.
