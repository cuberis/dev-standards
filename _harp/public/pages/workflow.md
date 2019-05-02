## Local Development

For all projects, developers should work locally before ever pushing code to a client facing or public site. Our preferred tool for local development is [Local by Flywheel](https://local.getflywheel.com/) which is geared specifically for WordPress. In instances where a non-WordPress environment is needed, our preferred tool is [Vagrant](https://www.vagrantup.com/).

## GitHub

All projects are managed using Git for version control along with GitHub for hosting the repositories. Projects under active development as well as proactive support should all have their own repos. Developers should be familiar with our standards for best practices when committing to one of our project repositories. For more information, [visit this page](/pages/git).

## Security

We take security of our team members as well as our clients very seriously. In turn, this influences a lot of aspects of our workflow. With that said, we recommend the following:

1. Always use secure connections when connecting to remote servers, i.e. SFTP/SSH (rather than regular FTP)
2. Always use strong passwords
3. Always use HTTPS, typically via Let's Encrypt
4. Avoid using commonly targeted usernames such as `root`, `admin`, `webadmin`, etc...
5. Use Two Factor Authentication (2FA) whenever available

## Deployments

_For contractors, see the [Contractors page](/pages/contractors)._

### Deploying Code

Anytime a developer is deploying code, it should be done with caution. No one every _purposefully_ deploys a piece of code not ready for a production environment so it is in everyone's best interest to take a few extra steps to ensure reliability of our deployments:

1. Never depoloy code that has not been tested locally
2. If you are deploying via automated deployments, ensure you are not deploying WordPress core or plugins and ensure all deployment paths are correct.
3. If using SFTP, ensure you are depoloying the correct files and in a logical order to avoid temporary `Function does not exist` errors.
4. If deploying code from a specific branch, make sure that branch does not contain any conflicting or missing code.
5. **NEVER, EVER** work directly on a production server 🤠

### Deploying Databases

As a general rule, we don't deploy databases. Exceptions to that rule would be for deploying a brand new site or in rare instances staging sites or development sites.

### Using DeployHQ

[DeployHQ](https://cuberis.deployhq.com/) is our go-to service for automated and more reliable deployments. It takes the headache out of remembering which files need to be uploaded and also syncs directly with GitHub for deploying straight from the code repository. As a general rule of thumb, we only use automated deployments for staging and dev servers, never the live production environment.