# CICD on Bitbucket

### Table of Contents
| No. | Questions |
| --- | --------- |  
| 1   | [Vuejs Frontend Website Deployment](#vuejs-forntend-website-deployment)  |  NA |
| 1.1 | [Bitbucket Pipeline](#bitbucket-pipeline)  |  NA |
| 1.2 | [Bitbucket Pipeline YAML SAMPLES](#bitbucket-pipeline-yaml-samples)  |  NA |
| 2   | [Docker File](#docker-file)  |  NA |

1. ### Vuejs Frontend Website Deployment

#### Bitbucket Pipeline 
👉 `bitbucket-pipelines.yml`

##### ⭐ Docker image options 
````
// public images
image:
  atlassian/default-image:latest

// private images
image:
  name: us-east1-docker.pkg.dev/my-project/my-repo/test-image:latest  // registered or stored in the cloud
  username: $DOCKER_REGISTRY_USERNAME
  password: $DOCKER_REGISTRY_PASSWORD
````

Image
- Property — image
- Required — No
- Data type — Either:
    - string
    - block of new-line separated key-value pairs

##### ⭐ Global options

````
options:
  max-time: 30
  docker: true
  size: 2x
````

Docker
- Property — docker
- Required — No
- Data type — Boolean
- Allowed values — true or false
- Default value — false

Max time
- Property — max-time
- Required — No
- Data type — Integer
- Allowed values — A positive integer between 1 and 120
- Default value — 120

Size
- Property — size
- Required — No
- Data type — String
- Allowed values — Either:
    - 1x or 2x for pipeline steps run on Bitbucket Cloud.
    - 1x, 2x, 4x, or 8x for pipeline steps run on a self-hosted pipeline runner.

##### ⭐ pipeline 

````
pipeline:
  Pipeline start options page
    parallel:
      Parallel step options page
    stage:
      Stage options page
    step:
      Step options page
````

Branches

````
image: node:lts
pipelines:
  default:
    - step:
        script:
          - echo "This script runs on all branches that don't have any specific pipeline assigned in 'branches'."
  branches:
    main:
      - step:
          script:
            - echo "This script runs only on commit to the main branch."
    feature/*:
      - step:
          image: openjdk:8 # This step uses its own image
          script:
            - echo "This script runs only on commit to branches with names that match the feature/* pattern."
````

The default section defines the default pipeline configuration, which applies to all branches that don't have specific pipeline configurations assigned. If a branch doesn't have a specific pipeline configuration defined in the branches section, the configuration from the default section will be used. In the provided example, the default section defines a step that runs on all branches that don't have specific configurations specified in the branches section.

The branches section allows you to specify pipeline configurations based on branch names. In the provided example, there are two branch configurations: main and feature/*. When code is committed to the main branch, the steps specified under the main branch are executed. Similarly, when code is committed to branches whose names match the feature/* pattern (e.g., feature/branch1, feature/branch2, etc.), the steps specified under the feature/* branch are executed.

Pull Requests

````
pipelines:
  pull-requests:
    feature/*:
      - step:
          name: Build for feature branch pull request
          script:
            - echo "Hello, feature branch PR!"
    hotfix/*:
      - step:
          name: Build for hotfix branch pull request
          script:
            - echo "Hello, hotfix PR!"
    '**':
      - step:
          name: Build for all other pull requests
          script:
            - echo "Hello, non-feature, non-hotfix pull request!"
````
(create pr)
Subsections like feature/* and hotfix/* define pipeline configurations for specific types of pull requests. For instance, for branches starting with feature/, a step named "Build for feature branch pull request" is executed, while for branches starting with hotfix/, a step named "Build for hotfix branch pull request" is executed.

The '**' subsection defines pipeline configurations for all other types of pull requests. This includes all branches not starting with feature/ or hotfix/. In the provided example, for these pull requests, a step named "Build for all other pull requests" is executed.

##### ⭐ definitions
````
definitions:
  Cache and service container definitions page
````

**[⬆ Back to Top](#table-of-contents)**

1.2 ### Bitbucket Pipeline YAML SAMPLES

````
image: albertcolom/ci-pipeline-php:7.1-alpine

pipelines:
  default:
    - step:
        caches:
          - composer
        script:
          - composer install
          - vendor/bin/phpcs --standard=PSR2 src
          - vendor/bin/phpunit
  branches:
    master:
      - step:
          caches:
            - composer
          script:
            - composer install
            - vendor/bin/phpcs --standard=PSR2 src
            - vendor/bin/phpunit
            - rsync -aclvrzp --delete --exclude .git/ -e "ssh -p22" ./ $STAGING_URL
    production:
      - step:
          caches:
            - composer
          script:
            - composer install
            - vendor/bin/phpcs --standard=PSR2 src
            - vendor/bin/phpunit
            - rsync -aclvrzp --delete --exclude .git/ -e "ssh -p22" ./ $PRODUCTION_URL
    feature/*:
      - step:
          caches:
            - composer
          script:
            - composer install
            - vendor/bin/phpcs --standard=PSR2 src
            - vendor/bin/phpunit
````

**[⬆ Back to Top](#table-of-contents)**

2. ### Docker File

**[⬆ Back to Top](#table-of-contents)**