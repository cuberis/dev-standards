All third-party contractors employed by Cuberis are required to follow the guidelines set forth in this website. If at any point a situation arrises where a deviation is warranted, please contact Cuberis before proceeding. Below are some general guidelines for contractors.

## Communication
Cuberis uses the Teamwork platform for both internal and client facing communication. Unless otherwise specified, contractors should ensure before posting a message/comment in Teamwork that it is only visible to Cuberis and **not** the client.

Cuberis Teamwork login - [https://cuberis.teamwork.com](https://cuberis.teamwork.com).

## Administration

Cuberis distinguishes between two kinds of work: projects and maintenance. Because we bill these two distinct kinds of work differently, time must always be logged under the proper category.

For employees, our Harvest time keeping system includes projects under each client's name. All project work should be logged to that account using the proper sub category. For all maintenance tasks we have set up a “Maintenance” client which has a list of every active client preceded with “MNT:”. All maintenance work needs to be logged to these accounts. For employees, your Harvest entries should always be rounded up to the nearest 15 minute increment. Use the Teamwork task name including the ID# in your descriptions.

For contractors, please report your time on projects separately from your time on maintenance tasks. You may report this time in any fashion you prefer, so long as each item is labeled as “project” or “maintenance.”

## Workflow

These steps are listed in order:

### 1. Work Locally
In all cases, local development is preferred. Work should never be done directly to a LIVE or Staging site, but coded and tested on a version of the site that lives on your local machine. See [Project Setup](/standards/pages/setup) for more information on getting setup.

### 2. Setting up a Staging Environment
In almost all cases, a staging site will be utilized to preview and QA code. A Cuberis team member will create the staging environment, however, it is up to the contractor to upload files and import databases as needed to the staging site.

### 3. Pushing to GitHub
A Cuberis team member will provide a repository for the project. This repository should be the single source of truth for a website's code base. Contractors should always work in their own separate branch, never in the DEV or MASTER branch. When work is ready to be pushed to staging, the branch can be pushed up and a Pull Request created. Pull Requests will be evaluated by a Cuberis Team member and merged into the appropriate branch when code is approved. A typical git workflow would be as follows:

```
cd into your local git repo
git checkout master
git pull origin master
git checkout -b [your-branch-name-here]

... do your work ...
... all changes are commited ...
... work is complete and ready to push ...

git push -u origin [your-branch-name-here]
```

Then on Github.com, visit the repo, and create a new Pull Request and notify a Cuberis team member. See [Git and GitHub](/standards/pages/git) for more information.

### 4. Deploying to Staging
Once a Pull Request has been successfully approved and merged, you may deploy the code to the staging site using your FTP/SFTP method of choice.

### 5. Deploying to LIVE site
Under no circumstances should code be pushed to a LIVE production site. Please contact a Cuberis team member for more information.
