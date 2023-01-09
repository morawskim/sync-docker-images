This repository contains GitLab CI/CD pipeline to sync container images between different repositories.
The main destination is Docker Hub, but Docker in past announced removes inactive images - https://www.docker.com/blog/scaling-dockers-business-to-serve-millions-more-developers-storage/

To sync images we use [patched version of skopeo](https://github.com/morawskim/skopeo-sync-patch), becaused images in GitLab container repository are stored in "username/project/container", but Docker Hub supports only "username/container".
During sync we append prefix (project name) to container name. In other words container "username/project/container" will be rename to "username/project-container".
