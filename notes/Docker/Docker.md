# DOCKER

Open-source container runtime. Uses "Dockerfile" to build image. Provides CLI.

Workflow: **Build, ship, run**. Turn software into image, put it in registry, then at where it runs, create container from image.

## Image (Build)

Universal app packager. Cross-OS, cross-platform, language agnostic.

### Dockerfile

Set of instructions to make image.

```dockerfile
FROM python
RUN pip install flask
WORKDIR /app
COPY ..
CMD python app.py
```

Every Dockerfile starts with `FROM`. Can start from someone else's image, can have multiple images. When Dockerfile is passed to `docker build`, commands inside build image layer by layer. E.g., this file starts with Python bins + libs layer at bottom, then Flask layer next, and app layer at top.

## Registry (Ship)

Universal app distribution. Each image has SHA hash. `docker push` pushes image to registry. Then on different machine, do `docker pull` to pull identical copy of that image.

## Container (Run)

Once image downloaded, `docker run` runs app on top of Docker (container runtime). Each container has own namespace, doesn't see rest of OS. If `docker run` same image again, creates another process, and two processes don't see each other.
