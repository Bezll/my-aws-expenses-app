# Project to explore Github Actions and AWS

The code in this repository was borrowed from a previous toy project I created some time ago.

My intention was to take this expenses app, host it on AWS, and then write an automation workflow for it.
So that on any commits to the master branch are automatically applied to the live site.

The purpose of this was to familiarise myself with the process of hosting a site on AWS, and creating Github Actions for automation. I have been studying backend and frontend at Northcoders, but I felt it would be also useful to explore some of the DevOps side of development.

## Writing the Workflow

When any of the files within this repository are updated and committed to the Github master branch. The workflow YAML file sets up a Virtual Machine and builds the project within this machine.

The script uses Checkout to ensure that the latest version of source code is being used,
and then dependencies are installed and the build is run.

The built project is then added to the AWS S3 bucket, secret access keys are saved in Github to allow authorisation.

## Flow chart

![flow chart]()

## Hosting on AWS

To host the app on AWS I first had to create an S3 bucket to hold all of the files.

I created a IAM (Identity Access Management) policy, to ensure that only the minimum access permissions would be granted.

Once this had been setup and the Github workflow had successfully pushed the files to the S3 bucket. I purchased the domain I wished to use for the app - www.expense-tracker.co.uk, from Route 53.

I requested an SSL certificate to verify security for HTTPS requests, and then wired my S3 bucket to CloudFront. This is then also routed to my new domain, adding in the relevant SSL certificate information.
