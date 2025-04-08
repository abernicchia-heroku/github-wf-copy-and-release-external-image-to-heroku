# GitHub Workflow to copy and release an external image to Heroku
This is an example of GitHub Workflow that allows you to copy a  docker image from an external container registry to the Heroku one and deploy it. The workflow can be manually executed via GitHub (workflow_dispatch).

It can be easily converted to a GitHub Action and integrated into more complex workflows.

# Supported Use Cases
- Docker images that are built and/or available externally and need to be deployed to Heroku
- Optimised copy registry-to-registry of docker images without requiring to pull and push the source image to Heroku

## Disclaimer
The author of this article makes any warranties about the completeness, reliability and accuracy of this information. **Any action you take upon the information of this website is strictly at your own risk**, and the author will not be liable for any losses and damages in connection with the use of the website and the information provided. **None of the items included in this repository form a part of the Heroku Services.**

## How to use it
Configure the workflow with the following variables/secrets:
  - `HEROKU_API_KEY` [required] Heroku API key used to create and deploy apps. Set it on GitHub as secret
  - `HEROKU_APP_NAME` [required] Deployed Heroku app name. Set it on GitHub as variable at repository level
  - `HEROKU_APP_FORMATION_TYPE` [required] Heroku formation type (e.g. web, worker, ...). Set it on GitHub as variable at repository level
  - `IMAGE_PLATFORM_TYPE` [required] Docker image platform type (e.g. linux/amd64). Set it on GitHub as variable at repository level
  - `CRANE_VERSION` [required] crane version to install (either latest or vX.Y.Z). Set it on GitHub as variable at repository level
  - `SRC_CONTAINER_REGISTRY_USER` [required] Source container registry user. Set it on GitHub as secret
  - `SRC_CONTAINER_REGISTRY_PASSWORD` [required] Source container registry password. Set it on GitHub as secret
  - `SRC_CONTAINER_REGISTRY_HOST` [required] Source container registry ushost. Set it on GitHub as variable at repository level
  - `SRC_CONTAINER_REGISTRY_IMAGE_URL` [required] Source image URL (e.g. myrepo/web). Set it on GitHub as variable at repository level
  - `DEST_CONTAINER_REGISTRY_USER` [required] Heroku container registry user (usually '_'). Set it on GitHub as secret
  - `DEST_CONTAINER_REGISTRY_PASSWORD` [required] Heroku container registry password (a Heroku auth key can be used). Set it on GitHub as secret

## Notes
- Currently tested on Heroku cedar and with linux/amd64 images only