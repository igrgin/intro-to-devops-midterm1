### Tasks and Solutions

---

### Task 1: Containerize the application based on the source code from GitHub.
**Solution:**
To containerize the application using Podman, follow these steps:
1. Clone the source code from the GitHub repository:
   ```bash
   git clone https://github.com/docker/getting-started-app
   ```
   - `git clone`: This command copies the repository from GitHub to your local machine.
2. Create a Dockerfile (or Containerfile if using Podman) in the root directory of the project.
3. Follow the guide at https://docs.docker.com/get-started/02_our_app/ but replace Docker commands with Podman equivalents.

---

### Task 2: Build the image and tag it with version 0.0.1.
**Solution:**
To build and tag the image, use:
```bash
podman build -t my-app:0.0.1 .
```
- `podman build`: Builds container images from a Dockerfile.
- `-t`: Specifies the tag for the built image.
- `.`: The build context, typically the directory containing the Dockerfile.

---

### Task 3: Inspect the image contents using Podman.
**Solution:**
```bash
podman image inspect my-app:0.0.1
```
- `podman image inspect`: Displays detailed information in JSON format about one or more images.

---

### Task 4: Review all available Dockerfile instructions.
**Solution:**
Visit the Dockerfile reference documentation at https://docs.docker.com/reference/dockerfile/ to understand all available instructions used in Dockerfiles.

---

### Task 5: Change the application message for no to-do items.
**Solution:**
Modify the source code to change the message displayed when there are no to-do items:
1. Edit the relevant source file to update the message. Instructions: https://docs.docker.com/get-started/03_updating_app/
2. Rebuild the image using the updated source code.

---

### Task 6: Build the image again and tag it with version 0.0.2.
**Solution:**
```bash
podman build -t my-app:0.0.2 .
```
- Uses the same command as for Task 2 but with a different tag to reflect the version change.

---

### Task 7: See the difference between the two images using the Podman diff command.
**Solution:**
```bash
podman diff my-app:0.0.1 my-app:0.0.2
```
- `podman diff`: Shows file system differences between two container images.

---

### Task 8: Create another repository on Docker Hub and push the images there.
**Solution:**
1. Log in to Docker Hub:
   ```bash
   podman login
   ```
2. Tag the images:
   ```bash
   podman tag my-app:0.0.1 username/my-app:0.0.1
   podman tag my-app:0.0.2 username/my-app:0.0.2
   ```
3. Push the images:
   ```bash
   podman push username/my-app:0.0.1
   podman push username/my-app:0.0.2
   ```

---

### Task 9: Create a Containerfile using the RHEL7 base image.
**Solution:**
Create a Containerfile:
```Dockerfile
FROM rhel7
RUN yum update -y && yum install httpd -y
CMD ["httpd", "-D", "FOREGROUND"]
```
   - `FROM`: Sets the base image.
   - `RUN`: Executes commands in a new layer on top of the current image.
   - `CMD`: Provides defaults for executing the container.
Build the image:
```bash
podman build -t myweb:0.0.1 .
```

---

### Task 10: Create a quadlet file to auto-start the container with the system.
**Solution:**
Refer to the guide at https://www.redhat.com/sysadmin/quadlet-podman to create and configure a quadlet file. This file is used with systemd to start containers automatically at system boot.

---

### Task 11: Build images using different Dockerfiles and compare sizes.
**Solution:**
1. Clone the repository:
   ```bash
   git clone https://github.com/jstanesic/example-go-app
   ```
2. Build images from different Dockerfiles:
   ```bash
   podman build -f Dockerfile1 -t example:Dockerfile1 .
   podman build -f Dockerfile2 -t example:Dockerfile2 .
   ```
3. Compare image sizes using:
   ```bash
   podman images
   ```
### Additional Reading
- https://docs.docker.com/reference/dockerfile/
- https://linuxhandbook.com/autostart-podman-containers/
- https://systemd.io/
- https://catalog.redhat.com/software/containers/rhel7/57ea8cee9c624c035f96f3af?architecture=amd64&image=65e70f46befb5000328d4d90
- https://github.com/nigelpoulton/psweb
- https://developers.redhat.com/articles/2023/05/17/build-lean-nodejs-container-images-ubi-and-podman
- https://earthly.dev/blog/docker-multistage/
- https://docs.docker.com/build/building/multi-stage/
- https://docs.bitnami.com/tutorials/optimize-docker-images-multistage-builds/
- https://earthly.dev/blog/docker-multistage/