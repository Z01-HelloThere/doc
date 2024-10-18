## Git main commands

### Configure Git (with GitHub)

[Connect to Github with a SSH key (Hello-There)](https://hello-there.org/others/security/add-ssh-key-github/)

### Init project

```javascript
git clone git@github.com:nicgen/forum.git
```

```javascript
git fetch --all
```

> `git fetch` is a command that retrieves updates from a remote repository but does not merge them with your local branch. It’s like downloading the latest changes without applying them directly to your working directory. The command fetches all the references (branches, tags, etc.) from the remote, allowing you to review or integrate those updates manually when you’re ready.

```javascript
git branch --all
```

```javascript
git switch <branchname>
```

### Working with branches

#### Create a branch

```javascript
git checkout -b "<branchname>"
```

for the first time you must set the new upstream branch:

```javascript
git push -u origin front/layout-add-login-register
```

> `-u` is an alias of `--set-upstream` 

#### Delete a branch

> It's a good idea to delete a branch in Git after you've merged it into another branch, such as the main or dev branch. This is because the changes from the deleted branch are still preserved in the branch that it was merged into, so you don't lose any history or changes.
> And it keeps your repository organized and clutter-free. If you have many branches that are no longer needed, it can be difficult to find the branches that are still relevant.

```javascript
# delete the remote branch (once you're sure that the branch is pushed in the remote )
git push -d <remote_name> <branchname>
# delete your local branch
git branch -d <branchname>
```

### Naming conventions

#### **Branch Names**

- Use descriptive and concise names for branches.
- Use lowercase letters and numbers.
- Avoid using special characters, except for hyphens (-) and underscores (_).
- Use a consistent naming convention throughout the repository.

Examples:

- `feature/new-login-system`
- `fix/bug-123`
- `release/v1.2.3`

#### **Commit Messages**

- Use the imperative mood (e.g., "Fix bug" instead of "Fixed bug").
- Keep the first line short (less than 50 characters).
- Use a blank line to separate the summary from the body.
- Use bullet points or paragraphs to explain the changes.

Examples:

- `Fix bug in login system`
- `Add new feature to dashboard`
- `Improve performance of database queries`

### Important commands

#### Retrieve

To retrieve the remote listing, changes, branches (without merging)

#### Commit



#### Push



#### Conflicts

Tools:

- [Meld](https://meldmerge.org/) ([install](https://flathub.org/apps/org.gnome.meld))



***

### Best practices

Here are the detailed recommendations with source links, especially for working with GitHub:

Best Practices:

1. Create a clear and concise commit message:

- Use the imperative mood (e.g., "Fix bug" instead of "Fixed bug").
- Keep the first line short (less than 50 characters).
- Use a blank line to separate the summary from the body.
- Use bullet points or paragraphs to explain the changes.
- [Source: GitHub documentation - Commit messages](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#commit-messages)

2. Use branches:

- Create a new branch for each feature or task.
- Use descriptive branch names (e.g., "feature/new-login-system").
- Keep the main branch (usually master) clean and stable.
- [Source: GitHub documentation - Branching and merging](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#branching-and-merging)

3. Use pull requests:

- Create a pull request to merge changes into the main branch.
- Use a descriptive title and description for the pull request.
- Assign reviewers to the pull request.
- [Source: GitHub documentation - About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)

4. Regularly pull and merge:

- Regularly pull changes from the main branch.
- Merge changes into your local branch.
- Use `git pull --rebase` to rebase your local branch on top of the main branch.
- [Source: GitHub documentation - Syncing your branch](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#syncing-your-branch)

5. Use GitHub Actions:

- Use GitHub Actions to automate workflows.
- Use GitHub Actions to run tests and build code.
- [Source: GitHub documentation - GitHub Actions](https://docs.github.com/en/actions)

6. Keep commits small:

- Break down large changes into smaller commits.
- Use `git add -p` to stage changes incrementally.
- Use `git commit --amend` to amend the previous commit.
- [Source: GitHub documentation - Committing changes](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#committing-changes)

7. Use descriptive branch names:

- Use descriptive branch names (e.g., "feature/new-login-system").
- Avoid using branch names that are too short or vague.
- [Source: GitHub documentation - Branching and merging](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#branching-and-merging)

8. Avoid committing unnecessary files:

- Use `.gitignore` to ignore unnecessary files.
- Avoid committing build artifacts or temporary files.
- [Source: GitHub documentation - Ignoring files](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#ignoring-files)

Working Correctly in a Group:

1. Communicate with your team:

- Use GitHub Discussions to discuss changes.
- Use GitHub Issues to track bugs and feature requests.
- [Source: GitHub documentation - GitHub Discussions](https://docs.github.com/en/discussions)

2. Use a consistent workflow:

- Establish a consistent workflow that everyone follows.
- Use GitHub Projects to track progress.
- [Source: GitHub documentation - GitHub Projects](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards)

3. Review each other's code:

- Use GitHub Code Review to review code.
- Use GitHub Code Review to leave comments and suggestions.
- [Source: GitHub documentation - Code review](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-code-review)

4. Use GitHub Teams:

- Use GitHub Teams to manage access and permissions.
- Use GitHub Teams to assign roles and responsibilities.
- [Source: GitHub documentation - GitHub Teams](https://docs.github.com)