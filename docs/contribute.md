# Contribute to the Hoplab Wiki

Welcome to the Hoplab Wiki repository. This Wiki is a work in progress and an ongoing effort to migrate all the Hoplab knowledge and procedures into a more user-friendly format. This process is currently managed by [@costantinoai](https://github.com/costantinoai) and [@kschevenels](https://github.com/kschevenels). For any questions, feel free to [ping me](mailto:andreaivan.costantino@kuleuven.be).

This guide will help you set up, update, and maintain the Wiki both locally and online. Follow the instructions if you want to make changes to the wiki.

!!! tip "Suggest or make quick edits"
    For most cases, if you want to **suggest some changes** you can do so by opening a [new Issue](https://github.com/HOPLAB-LBP/hoplab-wiki/issues/new). If you want to **make quick changes** to any page, you can do so by clicking on the **pencil icon (✏️)** at the top right of the page to begin editing the file.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Editing the Wiki](#editing-the-wiki)
    - [Adding a New Page](#adding-a-new-page)
    - [Creating Child Pages](#creating-child-pages)
    - [Adding Tags](#adding-note-todo-and-placeholder-tags)
    - [Common Formatting Syntax](#common-formatting-syntax)
    - [Linking and Referencing](#linking-and-referencing)
3. [How to Contribute](#how-to-contribute)
    - [Easy Workflow (Quick Changes)](#easy-workflow-for-quick-changes)
    - [Advanced Workflow (Extensive Changes)](#advanced-workflow-for-extensive-changes)
4. [Reviewing and Accepting Pull Requests (for Admins)](#reviewing-and-accepting-pull-requests-for-admins)
5. [Troubleshooting](#troubleshooting)

## Getting Started

Before you begin, ensure you have the following:

- A GitHub account (click [here](https://github.com/signup) to sign up).
- Be part of the [`HOPLAB-LBP`](https://github.com/orgs/HOPLAB-LBP/people) organization (contact [Andrea](mailto:andreaivan.costantino@kuleuven.be) if you need to be added).
- If you plan on following the [Advanced Workflow](#advanced-workflow-for-extensive-changes) (encouraged for more complex changes), also make sure that you have [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html), and [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) or [GitHub Desktop](https://desktop.github.com/) (strongly encouraged) installed.

## Editing the Wiki

We welcome contributions from all members. All the content of the wiki is written in Markdown files located in the `docs` directory. You can edit these files in your browser (if you follow the [Easy Workflow](#easy-workflow-for-quick-changes)) or locally using any text editor or IDE (e.g., VSCode, Sublime Text) if you follow the [Advanced Workflow](#advanced-workflow-for-extensive-changes).

### Adding a New Page

1. Create a new Markdown file in the `docs` directory (e.g., `docs/new-page.md`).
2. Add the new page to the `nav` section of `mkdocs.yml`:

```yaml
nav:
  - Home: index.md
  - Guide: guide.md
  - New Page: new-page.md
```

### Creating Child Pages

To create a child page, place the Markdown file in a subdirectory and update the `nav` section in `mkdocs.yml` accordingly:

1. Create a new subdirectory in the `docs` directory (e.g., `docs/subdir`).
2. Create a new Markdown file in the subdirectory (e.g., `docs/subdir/child-page.md`).
3. Update the `nav` section in `mkdocs.yml`:

```yaml
nav:
  - Home: index.md
  - Guide: guide.md
  - Subdir:
      - Child Page: subdir/child-page.md
```

### Adding `NOTE`, `TODO`, and `PLACEHOLDER` tags

For ease of collaboration, we keep track of all the tasks in our documentation in the [Issues](https://github.com/HOPLAB-LBP/hoplab-wiki/issues) page. Tasks are organized by file, and each file with tags will automatically be listed as Issue.

To add a new task to this list, you just need to write `NOTE`, `TODO`, or `PLACEHOLDER` in any document in the `docs/` folder. This will automatically be added to the Issue for that page during the Wiki building process. It is a good practice to write the name of the author in square brackets. Example:

`TODO: [Andrea] fix hyperlinks`

Please, remember to delete the source tag from the original file once the task is resolved. This will ensure that the Issue page includes only un-resolved tasks.

### Common Formatting Syntax

Here are some common Markdown elements:

- **Headers:** `# Header 1`, `## Header 2`, `### Header 3`, etc.
- **Bold text:** `**bold text**`
- **Italic text:** `*italic text*`
- **Links:** `[link text](URL)`
- **Lists:**
  - Unordered list: `- Item 1`
  - Ordered list: `1. Item 1`
- **Images:** `![Alt text](path/to/image.png)` (see [this section](#adding-and-linking-images) for instructions on how to link images.)

For more advanced formatting options, refer to the [MkDocs Material Reference Guide](https://squidfunk.github.io/mkdocs-material/reference/).

### Linking and Referencing

When creating or editing content, you may want to reference or link to other sections within the wiki, external resources, or images. Here's how to do it:

#### Internal Links (Within the Wiki)

Use relative paths for internal links. The general format is:

```markdown
[Link Text](path/to/file.md)
```

Examples:

1. Linking to a page in the same directory:

   ```markdown
   [Getting Started](getting-started.md)
   ```

2. Linking to a page in a subdirectory:

   ```markdown
   [fMRI Analysis](research/fmri/fmri-analysis.md)
   ```

3. Linking to a specific section on another page:

   ```markdown
   [Ethics Guidelines](research/ethics/index.md#ethical-guidelines)
   ```

4. Linking to a parent directory:

   ```markdown
   [Back to Research](../index.md)
   ```

#### External Links (Outside the Wiki)

For external links, use the full URL:

```markdown
[Hoplab Website](https://www.hoplab.be/)
```

#### Adding and Linking Images

When adding images to the Wiki:

1. Store all images in the `docs/assets` folder.
2. Use descriptive, lowercase names for images, separating words with hyphens (e.g., `fmri-analysis-workflow.png`).
3. Use relative links to reference images. The path depends on the location of your Markdown file:

    - If your Markdown file is in the main `docs` folder:

     ```markdown
     ![fMRI Analysis Workflow](../assets/fmri-analysis-workflow.png)
     ```

    - If your file is in a subdirectory of `docs` (e.g., `docs/research/`):

     ```markdown
     ![fMRI Analysis Workflow](../../assets/fmri-analysis-workflow.png)
     ```

    - If your file is in a sub-subdirectory (e.g., `docs/research/fmri/`):

     ```markdown
     ![fMRI Analysis Workflow](../../../assets/fmri-analysis-workflow.png)
     ```

4. Always include descriptive alt text for accessibility:

   ```markdown
   ![Diagram showing steps of fMRI analysis](../assets/fmri-analysis-workflow.png)
   ```

5. Optionally, specify image dimensions using HTML:

   ```html
   <img src="../assets/fmri-analysis-workflow.png" alt="fMRI Analysis Workflow" width="500">
   ```

#### Best Practices for Linking

1. Use descriptive link text that gives users an idea of where the link will take them.
2. Check your links after creating them to ensure they work correctly.
3. For external links, consider opening them in a new tab:

   ```markdown
   [Hoplab Website](https://www.hoplab.be/){target="_blank"}
   ```

4. When linking to specific sections within long documents, use anchor links to improve user experience.
5. For images, **always use relative links** and store images in the `docs/assets` folder to maintain a self-contained Wiki.

## How to Contribute

We offer two workflows for contributing to the Hoplab Wiki: an Easy Workflow for quick changes to single files, and an Advanced Workflow for more extensive changes to multiple files.

## Easy Workflow (for Quick Changes)

This workflow is ideal for making small, quick changes to a single file. It can be done entirely through your web browser and doesn't require any local setup.

In short, all you need to do is to navigate to the page you want to edit, **click the paper and pencil symbol** :material-file-edit-outline: at the top-right corner of the page, commit your changes and just follow the prompts. All the process is pretty much automated, and your changes will be merged when an admin approves them. For more information, see the box below and the rest of this section.

!!! tip "Edit directly from this page!"
    Existing pages can be edited directly through the Wiki! If you need to edit or add information to any page, look for the paper and pencil symbol :material-file-edit-outline: at the top-right of the page, next to the page title. This will make you edit the page and open a PR either by creating a new branch on the main repo (if you are part of the Hoplab organization on GitHub) or by forking your own copy of the repo (if you are an external contributor). Make sure to [submit a PR](#step-3-submit-a-pull-request-pr-with-your-proposed-changes) after your changes are made.

### Step 1: Make Your Changes

1. **Editing an Existing Page:**

    - Navigate to the [`HOPLAB-LBP/hoplab-wiki`](https://github.com/HOPLAB-LBP/hoplab-wiki) repository.
    - Click on the file you want to edit (usually found under the `docs/` directory).
    - Select the **pencil icon (✏️)** at the top right to begin editing the file.

2. **Creating a New Page:**

    1. **Reference the page in `mkdocs.yml`:**

        - Go to the `mkdocs.yml` file in the repository.
        - Click on the **pencil icon (✏️)** to edit the file.
        - Add the new page (e.g., `docs/new-page.md`) to the `nav` section in `mkdocs.yml` to make it visible in the site navigation.
        - After editing `mkdocs.yml`, follow the steps in **[Step 2](#step-2-commit-changes-to-a-temporary-branch)** below to commit and create a new branch.

    2. **Creating the New File:**

        - Once your new branch is created (see [Step 2](#step-2-commit-changes-to-a-temporary-branch)), navigate to the `docs/` folder in this branch.
        - Select **Add file** > **Create new file**.
        - Name the file according to the path you specified in `mkdocs.yml` (e.g., `docs/new-page.md`).

After creating or editing the page, you can add content in Markdown format. To preview your changes, click **Preview** next to the **Edit** tab.

![](assets/contribute-commit.png)

!!! warning
    Some features -- like admonition boxes (such as this one), tabs, and cards -- are specific to [mkdocs material](https://squidfunk.github.io/mkdocs-material/reference/) and will not be rendered correctly in the GitHub preview. You can preview your changes in your browser locally (before committing) only by following the [Advanced Workflow](#advanced-workflow-for-extensive-changes)

### Step 2: Commit Changes to a Temporary Branch

1. Once edits are complete, click **Commit changes**.
2. In the pop-up window, enter a **commit message** and a short **description** of your changes.
3. Select **Create a new branch for this commit and start a pull request**.
4. Click **Propose changes**.

![](assets/contribute-propose.png)

This process creates a [new branch](https://github.com/HOPLAB-LBP/hoplab-wiki/branches) that includes your changes. The branch name will typically be named something like `yourname-patch-1`.

!!! question "Why Use a Separate Branch?"
    Using a separate branch for your edits allows you to:

    - **Review and refine** changes before they are applied to the main repository.
    - **Collaborate with others**, requesting feedback or further edits.
    - **Organize related edits** to multiple files as part of one update.

Upon creating a branch in our repository, a [pull request (PR)](https://github.com/HOPLAB-LBP/hoplab-wiki/pulls) will automatically open (see [Step 3](#step-3-submit-a-pull-request-pr-with-your-proposed-changes) for more on PRs). The PR will contain all commits in the branch.

If you need to make additional edits related to the same update (e.g., creating a new page and updating `mkdocs.yml` to reference it), commit these changes to the same branch. This approach ensures that all related edits are grouped under a single PR, making it organized and easy to review.

??? question "Where do I find my new branch?"
    You can find your branch in the [branches list](https://github.com/HOPLAB-LBP/hoplab-wiki/branches).

    ![Branches list](assets/contribute-branches.png)

!!! note "Adding Multiple Commits to a Single PR"
    Any commits you make to `yourname-patch-1` will automatically be included in the same pull request linked to this branch, which keeps all related changes in one place for easy review.

### Step 3: Submit a Pull Request (PR) with Your Proposed Changes

1. In the "Open a pull request" page, add a **descriptive title** and a **summary** of your changes.
2. On the right side, assign an admin reviewer (currently [@costantinoai](https://github.com/costantinoai)).
3. Click **Create pull request** to submit your changes.

![](assets/contribute-open-pr.png)

!!! tip "Adding More Changes to an Open PR"
    If additional changes are needed for an already open PR, there’s no need to open a new one. Simply go to the branch created for your PR (available in the [branches list](https://github.com/HOPLAB-LBP/hoplab-wiki/branches)) and continue editing your files within this branch.

    - Choose **Commit directly to the `<branch-name>` branch** instead of creating a new branch for these edits.
    - If planning to add multiple commits to a PR, wait to assign a reviewer until all changes are complete, or **use a draft PR** until your updates are finalized. This prevents accidental early merges.

Following these steps will add a new branch to the repository, visible in the [branches list](https://github.com/HOPLAB-LBP/hoplab-wiki/branches), and a corresponding PR in the [pull requests list](https://github.com/HOPLAB-LBP/hoplab-wiki/pulls). Once approved by at least one reviewer and merged into the main branch, the branch will be automatically deleted, and your changes will be live.

## Advanced Workflow (for Extensive Changes)

The preferred way to contribute if you need to make **significant/multiple changes**, but it requires some familiarity with git, Python, and Conda environments. If you are not a Wiki maintainer, this workflow is probably overkill.

With this workflow, you will make and preview all the edits locally (on your computer). This allows for more control and flexibility, as it lets you see your changes in a live session.

!!! question "How should I organize my PR?"
    A [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) (or PR) "*is a proposal to merge a set of changes from one branch into another*". Ideally, a PR should include all the commits **for a specific feature** or bugfix from end-to-end. Avoid making PRs that contain multiple unrelated changes. For instance, if you are working on a feature that requires modifications across multiple files, ensure all those changes are included in the same PR. Conversely, avoid combining changes for different features (e.g., adding unrelated updates to the fMRI workflow and the getting started section) in a single PR. Each PR should represent a cohesive unit of work.

Here's a step-by-step guide that includes forking and cloning the repository, making and testing changes locally, and then submitting those changes for review through a pull request.

### Step 1: Forking the Repository and Cloning Your Fork

=== "Using the CLI"

    1. **Navigate to the Original Repository:**
        
        Open your web browser and go to the GitHub page for the `hoplab-wiki` repository located under the `HOPLAB-LBP` organization.
    
    2. **Fork the Repository:**
        
        Click the "Fork" button at the top right corner of the repository page. This will create a copy of the repository under your GitHub account.
    
    3. **Clone Your Fork:**
        1. Click the "Code" button on your forked repository page and copy the URL.
        2. Open your terminal (Command Prompt on Windows, Terminal on macOS and Linux) and navigate to the directory where you want to store the project, then type:
           ```bash
           git clone https://github.com/your-username/hoplab-wiki.git
           ```
        3. Change into the directory of the cloned repository:
           ```bash
           cd hoplab-wiki
           ```

=== "Using GitHub Desktop"

    1. **Navigate to the Original Repository:**
    
        Open your web browser and go to the GitHub page for the `hoplab-wiki` repository located under the `HOPLAB-LBP` organization.
        
    2. **Fork the Repository:**
    
        Click the "Fork" button at the top right corner of the repository page. This will create a copy of the repository under your GitHub account.

    3. **Open GitHub Desktop:**
    
        If you do not have GitHub Desktop installed, download and install it from [GitHub Desktop's official website](https://desktop.github.com/).

    3. **Clone Your Fork Using GitHub Desktop:**
        1. Open GitHub Desktop.
        2. In the top menu, click on `File > Clone Repository`.
        3. In the "URL" tab, paste the URL of your forked repository from your GitHub account into the "Repository URL" field.
        4. Choose the local path where you want to store the repository on your computer.
        5. Click "Clone".

### Step 2: Setting Up Your Local Environment

1. **Install Conda:**

    If you don't have Conda installed, download and install it from [Conda's official website](https://docs.conda.io/en/latest/miniconda.html).

2. **Create and Activate a Conda Environment:**

    ```bash
    conda create --name hoplab-wiki python=3.9
    conda activate hoplab-wiki
    ```

3. **Install Necessary Packages:**

    ```bash
    pip install mkdocs mkdocs-material mkdocs-git-revision-date-localized-plugin mkdocs-git-authors-plugin
    ```

### Step 3: Making Changes

1. **Edit Documentation:**
     You can now make changes to your local clone of the documentation. Use a text editor or an IDE to open and edit the Markdown files in the repository. If changes are extensive, consider splitting them into smaller, manageable commits that focus on specific pages or sections for clarity and ease of review.

### Step 4: Testing Your Changes Locally

1. **Serve the Documentation Locally:**
   1. While in your project directory and with the Conda environment activated, launch the local server by typing:

      ```bash
      mkdocs serve
      ```

   2. Open a web browser and navigate to `http://127.0.0.1:8000/`. This allows you to see your changes as they would appear on the live site.
   3. Keep this server running as you make changes; refresh your browser to update the preview.

### Step 5: Closing the Local Server

1. **Stop the Server:**
    When you are done previewing and editing and you are done with the changes, go back to the terminal where your server is running and press `Ctrl+C` to stop the server.

### Step 6: Committing Your Changes

=== "Using the CLI"

    1. **Stage and Commit Your Changes:**
        1. From your terminal, navigate to the main folder of the repo `cd hoplab-wiki`
        2. Add all modified files to your commit:
          ```bash
          git add .
          ```
        3. Commit the changes, including a clear message about what was modified and why:
          ```bash
          git commit -m "Detailed description of changes"
          ```
    2. Push your commits to the forked repository on GitHub:
          ```bash
          git push origin main
          ```

=== "Using GitHub Desktop"

    1. **Stage and Commit Your Changes:**
        1. In GitHub Desktop, you should see the list of changed files in the left sidebar.
        2. Review the changes by clicking on each file.
        3. Once you are ready to commit, write a summary of the changes in the "Summary" field at the bottom left.
        4. Add a more detailed description in the "Description" field if necessary.
        5. Click the "Commit to main" button.
        
    2. **Push Your Changes:**
        1. In GitHub Desktop, click on the `Push origin` button at the top to push your commits to GitHub.

### Step 7: Creating a Pull Request

1. Navigate to your forked repository on GitHub.
2. Click on the "Pull requests" tab.
3. Click on "New pull request".
4. Choose the original repository's `main` branch as the base, and your fork's `main` branch as the compare.
5. Fill out the form to describe the changes.
6. In the right panel, make sure to assign an admin (as of July 2024, [@costantinoai](https://github.com/costantinoai)) to review your changes.
7. Click on "Create pull request" to submit your changes.

!!! note "Automatic Deployment with GitHub Actions"
    This repository is set up to use GitHub Actions for automatic deployment. This means that every time changes are merged into the `main` branch, the documentation will automatically be built and deployed to GitHub Pages. You do not need to manually run the `mkdocs gh-deploy` command each time you make changes. Simply push your changes to the `main` branch, and GitHub Actions will handle the deployment.

### Reviewing and Accepting Pull Requests (for Admins)

1. Go to the `hoplab-wiki` repository on GitHub.
2. Click on the "Pull requests" tab.
3. Review the pull request (Approve changes or suggest edits)
4. When the changes are satisfactory, approve the changes and click "Merge pull request". This will delete the temporary branch.

## Troubleshooting

### Permission Denied or Authentication Issues

If you encounter issues with pushing to the repository, you may need to use a personal access token. Follow these steps:

1. Create a fine-grained personal access token [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token).
2. Use this token for authentication when pushing to the repository. More information on how to do so can be found on [this issue](https://github.com/shiftkey/desktop/issues/217#issuecomment-934660228). Please, first get a fine-grained Personal Access Token as described in the link above, and then follow the instructions in the "Manually temporary resolving this issue for a single git repository" section.

### Additional Help

For further assistance, refer to the following resources:

- [MkDocs Documentation](https://www.mkdocs.org/)
- [MkDocs Material Theme](https://squidfunk.github.io/mkdocs-material/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

Or [ping](mailto:andreaivan.costantino@kuleuven.be) me.

Thank you for contributing to the Hoplab Wiki!
