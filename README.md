# Gitlab-CI Docker pipeline

A real and simple pipelines example using gitlab-ci for building docker image, pushing to ECR, and restarting ECS services.
The idea is to be a fully continuos deployment approach on every commit to develop or master.

## Approach

In this case there are two steps:
- build
- deploy

And there are two pipelines:
- build/deploy to staging from develop/release/staging branches
- build/deploy to prod from master branch

## Infrastructure and config used

- ECR: for storing docker images
- ECS: where services are running

Task definitions on both environments of the service are pointing to fixed tags, so there is no need to create new ones (and assign to the service) on every deploy.

- staging is pointing to latest_staging
- prod is pointing to latest_prod

## Config

For using this pipelines needs to:
- have the proper services, cluster, ecr names  on the gitlabi-ci.yml (were changed for the example)
- set the AWS credentials on gitlab-ci console (check not to show them on the log)

