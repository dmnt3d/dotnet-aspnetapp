# REFERENCE:
https://www.acloudjourney.io/blog/buildpacks-a-net-developers-perspective

# Microsoft DotNet Samples
https://github.com/dotnet/dotnet-docker


# traditional DockerFile
docker build --pull -t aspnetapp:alpine -f Dockerfile.alpine-x64 .
docker run --rm -it -p 8000:80 aspnetapp:alpine

# paketo
pack build aspnetapp:paketo --builder paketobuildpacks/builder:base
## RUN:
docker run --rm -it -p 8000:8080 aspnetapp:paketo

# TBS:
## Imperative:
kp image create dotnet-aspnetapp --tag index.docker.io/dmnt3d/dotnet-aspnetapp --cluster-builder default --sub-path aspnetapp --git  https://github.com/dmnt3d/dotnet-aspnetapp.git --git-revision main


## Declarative
k apply -f image.yaml 

### watch the build:
kp build list spring-petclinic
kp build logs spring-petclinic
k describe image spring-petclinic

kp image status spring-petclinic

## Run:
docker run --rm -it -p 8080:8080 dmnt3d/dotnet-aspnetapp
 

# Kubernetes
## Scale deployment
- change replica

# Trigger build:
Index.cshtml