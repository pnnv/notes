##### Open Source project checklist
- [ ] License
- [ ] Latest Commit
- [ ] Number of contributors
- [ ] Frequency  of contributions
- [ ] Number of open issues
- [ ] How quickly do the maintainers respond to the issues
- [ ] Active discussion on issues
- [ ] Are issues getting closed ?
- [ ] Number of open pull requests
- [ ] Maintainers' response to the pull requests
- [ ] Recency of the pull requests
- [ ] How recently were the pull requests merged?

#### Contributing on Github
- **Fork the repository** and clone it locally. Connect your local to the original "upstream" repository by adding it as a remote. Pull the changes from "upstream" often to stay up to date so when you submit the pull request, merge conflicts will be less likely.
```shell
git clone https://github.com/YOUR-USERNAME/Spoon-Knife
> Cloning into `Spoon-Knife`...
> remote: Counting objects: 10, done.
> remote: Compressing objects: 100% (8/8), done.
> remove: Total 10 (delta 1), reused 10 (delta 1)
> Unpacking objects: 100% (10/10), done.
```
- **Creating a branch to work on**
```shell
git branch BRANCH-NAME
git checkout BRANCH-NAME
```
- **Making and pushing changes**
Go ahead and make a few (helpful) changes in your favourite text editor.
When you are ready to submit changes, stage and commit your changes `git add .` tells Git that you want to include all of your changes in the next commit. `git commit` takes a snapshot of those changes.
```shell
git add .
git commit -m "a short description of the change"
```
Right now these changes only exist locally. When you are ready to push your changes up to GitHub, push your changes to the remote.
```shell
git push
```

- Making a **pull request**
When you are ready to propose changes to the main project, this is the most important step. Visit the main project repository on Github, click **contribute** and then **Open a pull request**.

Github will bring up a page that shows the differences between your fork and the main project