# QA Cloud Custodian

[![QA Custodian](https://github.com/slickwarren/rancher-qa-tasks/actions/workflows/main.yaml/badge.svg)](https://github.com/slickwarren/rancher-qa-tasks/actions/workflows/main.yaml)

QA custodian will clean up resources in AWS, GCR, and AZURE. Currently, we have:
* AWS
  * instances
  * NLBs

### Getting Started
New Hires - make a PR adding one line to the `user-keys.txt` file. Use that key in ALL resources you create when using SUSE resources.  Keep it short (6 characters or less) unique to you, and recognizable by others (And, this is case sensitive!). For example, if your name was Melissa Di Donato, something like `mdd` would suffice. Just make sure you can remember it, and others can know who's it is if they are on your team. 

### About the Automation
This suite is setup to run with [Github Actions](https://docs.github.com/en/actions) on a cron schedule.  This is a free to use service, up to 2000 minutes of runtime per month. Navigate to this repo's `Actions` page, and click the latest run to view build info, logs, and more.
##### Is It Secure?
We use github secrets, which are only accessible to the maintainers (users with write access) of the repo.  However, just as with any other policy that is publically accessible, there are risks. We should be sure to never merge any code that outputs a secret.

### About the Code
This suite is fairly simple, and runs using [Cloud Custodian](https://cloud-custodian.github.io/cloud-custodian/docs/quickstart/index.html). Our modifications consist of the following:
* text files
  * `*-keys.txt` representing special keys that correspond with QA's resources
  * `regions.txt` (AWS explicit) representing the regions we use on a regular basis, and therefore what the custodian will check against 
* `.yaml` files, which are different configurations for the custodian to use when running. 