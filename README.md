# GDPR Consent

## What?

This repository is created solely for the purpose of generating JSON templates that are used by Identity Service by proxying the template content from S3 to the customer.

## How?

There is a circle-ci container that is run that injects the translations in the templates and injects it when needed.

1. There is a hook that is configured in crowdin to notify us when translations are updated.

2. When the hook gets called then we:
  - get latest translations from crowdin
  - commit changes to the repository
  - trigger a build in circle ci

3. The build in circle CI takes latest sources commited to master and 💥 they get uploaded to S3.

## Why? 

We need to decouple the upload from the Identity Service.
