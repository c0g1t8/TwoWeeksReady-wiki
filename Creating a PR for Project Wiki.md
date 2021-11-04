# Creating a PR for Project Wiki

Github Wikis can be configured such that they can only be edited by designated collaborators. This prevents other users from changing the Wiki content without a review process.

In order to contribute to the Wiki, you will need an editable copy of the Wiki repository. Once you are satisfied with your changes, submit a PR with a link to your repository.

```Powershell
# clone
git clone https://github.com/HTBox/TwoWeeksReady.wiki.git TwoWeeksReady-wiki
# rename origin so that changes from the project wiki can be fetched
cd .\TwoWeeksReady-wiki\
git remote rename origin htbox
# create a new repository
# this will automatically add an origin that points to the new repository
gh repo create TwoWeeksReady-wiki -y
# push wiki to new repository
git push -u origin master
# check remote settings
git remote -v
```

You should get the following with the _origin_ pointing to your copy of the wiki repository:

```Powershell
htbox   https://github.com/HTBox/TwoWeeksReady.wiki.git (fetch)
htbox   https://github.com/HTBox/TwoWeeksReady.wiki.git (push)
origin  https://github.com/c0g1t8/TwoWeeksReady-wiki.git (fetch)
origin  https://github.com/c0g1t8/TwoWeeksReady-wiki.git (push)
```

_Pull Requests_ must be handled through the Issues system since this requires one of the collaborators to first accept the PR to their local copy of the Wiki before pushing it up to the project.
