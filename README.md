# docker-cheatsheet

## Docker Workflow
<details>
<summary>See details</summary>

```
A common Docker workflow, particularly in software development and CI/CD pipelines, involves several key stages that
help automate the deployment and ensure consistency across environments. Here's a high-level overview of these stages,
including the typical commands and practices involved:

================================
1. Development and Local Testing
================================
Dockerfile Creation: The process begins with writing a Dockerfile, which defines how the Docker image is built.
It includes the base image to use, software to install, and configuration settings.
Local Image Building: Developers use docker build to create Docker images locally from their Dockerfiles. This allows
for immediate feedback on whether the Docker image is set up correctly.
Local Container Running: After building the image, developers run the container using docker run to test locally.
This step is crucial to ensure the application functions as expected in the isolated Docker environment.

==================================
2. Integration into CI/CD Pipeline
==================================
Automated Image Building: In a CI/CD pipeline, automated tools trigger docker build commands to create Docker images
whenever there's a commit or update in the source code repository.
Automated Testing: Once the image is built, automated tests are run inside Docker containers to validate functionality,
performance, and security. This might involve unit tests, integration tests, and other forms of automated checks.

=============================
3. Image Registry Interaction
=============================
Pushing to Registry: If the automated tests pass, the Docker image is pushed to a Docker registry using docker push.
This registry could be a public one like Docker Hub or a private one like Amazon ECR or Azure Container Registry.
Version Tagging: Images are typically tagged with version numbers or git commit hashes to manage different versions of
the application and to rollback if necessary.

=============
4. Deployment
=============
Pulling from Registry: Deployment environments pull the Docker image from the registry using docker pull. This ensures
that the exact same image tested in CI is deployed in production.
Container Orchestration: For applications that require multiple containers or need to scale, orchestration tools like
Kubernetes, Docker Swarm, or Amazon ECS are used. These tools manage the deployment, scaling, and networking of containers.

=========================
5. Monitoring and Logging
=========================
Runtime Monitoring: Once containers are deployed, monitoring tools are used to keep track of the container’s health, usage
metrics, and performance. Docker stats or third-party tools can provide insights.
Logging: Proper logging mechanisms are established to capture logs from containers. These logs are essential for troubleshooting
and understanding application behavior in production.

==========================
6. Security and Compliance
==========================
Image Scanning: Docker images are scanned for vulnerabilities and compliance issues using tools like Clair, Trivy, or
proprietary scanners provided by the registry services.
Security Best Practices: Implement security best practices such as using minimal base images, avoiding running containers
as root, and keeping secret data out of the image.

==========================
7. Cleanup and Maintenance
==========================
Prune Unused Images and Containers: Regular cleanup tasks like docker system prune can be run to remove unused Docker objects,
which helps in managing resources and keeping the environment clean.

================================
Example Workflow Command Summary
================================
Develop > docker build > docker run (local tests)
Commit > Trigger CI > docker build > Automated tests
Pass tests > docker push to registry > docker pull in production > Deploy with Kubernetes/Docker Swarm
Monitor > Log > Security scan > Clean up with docker system prune
These steps, although customizable based on specific needs and tools, represent a comprehensive Docker workflow that ensures
development practices are aligned with production deployment, leading to more reliable and maintainable applications.
```  
</details>

<hr>

## Docker init 
Use this to create boilerplate Docker files!
<br>[Blog](https://spacelift.io/blog/docker-init#how-to-use-docker-init--example-)

<hr>

## Google Cloud Lab
<pre>
gsutil cp gs://&ltbucketname&gt/&ltdestination&gt
tar zxvf &ltname_of_tarred_dockerfiles&gt
docker build -t "&ltusername?/&limage_name&gt:&lttag&gt" .
gcloud auth configure-docker
docker push &ltusername&gt/&ltimage_name&gt:&lttag&gt
  
From GUI, play around with scale and hitting app using its public endpoint
</pre>

<hr>

## Useful gcloud commands
<pre>
GET
gcloud auth list
gcloud config list project
gcloud auth list
PUSH
</pre>
