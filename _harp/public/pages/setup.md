
### Setting up a Local Development Environment

Cuberis generally uses one of 2 environments for setting up a local development project:

#### WordPress Development

1. [Local by Flywheel](https://local.getflywheel.com/)
2. [Vagrant](https://www.vagrantup.com/) + [Varying Vagrant](https://github.com/Varying-Vagrant-Vagrants/VVV)

#### PHP Development

1. [Vagrant](https://www.vagrantup.com/)


While these tools are preferred Cuberis works to continually evaluate the best tool for internal projects as well as project needs.

### The GitHub Repo

Any new or maintenance project gets a GitHub repo for code storage and management. To create a new repository a Development Team Member will log into Github and with in the Cuberis account create a new repository.

Once the new repo is created the developer can make their initial commit.

If creating a new project the initial commit should include baseline boilerplate files for the project which may include basic WP or Drupal files along with any other frameworks or plugins that are part of project baselines. This initial commit should take place before any additional CSS, JS or HTMl are added to the project.

If the repo is for a maintenance account or a new support client the initial commit should include all files as they were initially provided, before any updates or changes are made.

#### .gitignore Files

Using an appropriate .gitignore file is critical.

For an example of our default WordPress .gitignore file, see our [Base Theme .gitignore](https://github.com/cuberis/cuberis-base/wiki/Default-.gitignore).

#### Branches

Cuberis has a specific branching structure for developing, staging and shipping code.

**Development**

The primary primary branch for Development is the 'dev' branch. This branch should only ever have working code and should be the primary branch that work is merged into.

The 'dev' branch as sub branches labeled to indicate purpose.
- **bug/branch-name** : These branches are specifically for dealing with a collection of smaller bug, they may be ended with the day the work is being done or the type of work, ie. jan26, css-updates, js-errors.
- **issue/issue-number** : Branches prepended with issue/ are for specific larger scale issues reported in Github.
- **feature/feature-name** : These branches are used in primary production as well as for ongoing development of new features. There may be more than one of these branches to a feature as one may include backend or functional code while the other contains frontend.
- **styles/general** : This branch and associated branches are for the creation and implementation of general purpose CSS/JS that are not directly associate with specific components.

**Staging**

The 'staging' branch does not have sub branches. This branch primary serves as a testing, and staging branch before anything is pushed to production. Code may sit in this branch until reaching an appropriate deployment branch when it is merged to master.

**Production**

The 'master' branch does not have sub branches. This branch should never be edited and is should be a direct representation/duplication of the code that is in production for any given project. As our deployments are triggered by any push to this branch it is critical that code be properly tested before being merged into master. Merges should only take place as a pull request from staging.
