# Contributing to Substratum development

We openly welcome patches for both the OMS framework and the Substratum application.
Framework changes (including Theme Interfacer) are done through our [Gerrit](https://substratum.review/) and changes
to the Substratum app are done via pull requests. This will go over how to
properly push your changes.

# Submitting framework changes

These will include new framework features and exposures.

Our framework changes are hosted at our [SubstratumResources organization](https://github.com/SubstratumResources). [Theme Interfacer](https://github.com/substratum/interfacer) changes are also done though Gerrit.

### 1. Set up your Gerrit account

1. Go to the [Substratum Gerrit](https://substratum.review/)
2. Click the sign in button in the upper left-hand corner
3. Sign in with your Google account
4. Click the avatar/name in the upper left-hand corner
5. Create a username (this is permanent so choose wisely)

### 2. Generate SSH keys and add them to your account

Follow [Github's guide](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) for generating SSH keys. Once you have generated those keys,
go to our Gerrit, go to the same account settings page as above, click on the
SSH Public Keys section, and add the full contents of the ~/.ssh/id_rsa.pub file
that was generated.

### 3. Clone the repo you want to change

Clone the repo from the link above. Everything is currently done on our o branch for the framework

```bash
git clone -b o <repo_url>
```

Example:
```bash
git clone -b o https://github.com/SubstratumResources/platform_frameworks_base
```

### 4. Make and commit your changes

```bash
git add -A
git commit
```

Always make sure to make the commit message as detailed as possible. Also be sure
to keep authorship intact if you had to manually add someone else's work.

If you haven't committed the change yet:
```bash
git commit --author="Name <email>"
```

If you have committed the change
```bash
git commit --amend --author="Name <email>"
```

Once your commit is in good shape, add a change ID:

```bash
curl -Lo .git/hooks/commit-msg https://substratum.review/tools/hooks/commit-msg
git commit --amend
```

Without this commit ID, you cannot push to Gerrit.

### 5. Push the change!

The push command takes the following format:

```bash
git push ssh://<USERNAME>@review.projektsubstratum.com:29418/<PROJECT> HEAD:refs/for/<BRANCH>
```

Our list of projects are available [here](https://substratum.review/#/admin/projects/).

Example:
```bash
git push ssh://nathanchance@substratum.review:29418/SubstratumResources/platform_frameworks_base HEAD:refs/for/o
```

If you need to make any changes to your patch, use `git commit --amend` then push
again using the same command as above. Creating a new commit will push a new
change. Also be sure not to change the commit ID.

### 6. Add reviewers

In order to have your change accepted into the Substratum repos, it will need to
be reviewed by Substratum team members and members of the community. The following
members have global merge rights and can review patches across all repos:
+ [George G.](https://github.com/KreAch3R)
+ [Harsh Shandilya](https://github.com/MSF-Jarvis)
+ [Ivan Iskandar](https://github.com/iskandar1023)
+ [Nathan Chancellor](https://github.com/nathanchance)
+ [Nicholas Chum](https://github.com/nicholaschum)
+ [Surge Raval](https://github.com/Surge1223)
+ [Syko Pompos](https://github.com/sykopompos)

All of the team will check Gerrit periodically but Harsh, Ivan, Nathan, Nick,
and Surge are more active so adding one of them will give your patch a higher chance of
getting merged quicker. They will assign your patch with a review, the meaning
of which can be viewed [here](https://gerrit-review.googlesource.com/Documentation/config-labels.html#label_Code-Review)
and [here](https://gerrit-review.googlesource.com/Documentation/config-labels.html#label_Verified).


# Submitting application changes

Be sure you know [how to build the Substratum APK](BuildingSubstratum.md) before attempting this.

### 1. Fork the Substratum application

Go to the [Substratum repo](https://github.com/substratum/substratum) and click on the fork button then select where you want
the fork to reside.

### 2. Make and commit your changes

```bash
git add -A
git commit
```

Always make sure to make the commit message as detailed as possible. Also be sure
to keep authorship intact if you had to manually add someone else's work.

If you haven't committed the change yet:
```bash
git commit --author="Name <email>"
```

If you have committed the change
```bash
git commit --amend --author="Name <email>"
```

### 3. Pull request the change

1. Go to the Substratum repo page and click on the "New pull request" button.
2. Click the blue "compare across forks" text.
3. Find your fork in the list.
4. If you need to comment on your changes further than the commit message does, add them to this text.
5. Submit the pull request


# Some final notes

We cannot promise that every change will be merged but we will evaluate the changes
that are pushed in a fair manner. Theme template changes can be submitted in the
same manner as the Substratum app.

If you would like to discuss development with us in depth, please reach out using the information in the main README to join our Slack.