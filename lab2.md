### Tasks and Solutions

---
**1. Connect to the workstation VM inside RH Academy lab environment.**
- **Solution:** Connect to the VM via SSH or through the provided RH Academy portal interface.
  - **Command:**
    ```bash
    ssh student@vm-ip-address
    ```
  - **Explanation:** Use your RH Academy credentials to access the virtual machine.

---

**2. Use Podman to find the latest nginx container image from Docker Hub.**
- **Solution:** Search for all images related to "nginx" on Docker Hub.
  - **Command:**
    ```bash
    podman search nginx
    ```
  - **Explanation:** This command queries Docker Hub for available nginx images.

---

**3. Locate the documentation for the nginx image.**
- **Solution:** Documentation is often available directly on the Docker Hub page for the nginx image.
  - **Explanation:** Official images on Docker Hub typically include documentation links.

---


**4. List running containers on the system.**
- **Solution:** List all currently running containers.
  - **Command:**
    ```bash
    podman ps
    ```
  - **Explanation:** This command displays all containers that are currently running.

---


**5. Pull the identified nginx image using Podman.**
- **Solution:** Pull the latest version of the nginx image from Docker Hub.
  - **Command:**
    ```bash
    podman pull nginx:latest
    ```
  - **Explanation:** This command downloads the latest nginx image to your local system.

---


**6. Obtain detailed information about the nginx container image.**
- **Solution:** Display detailed information about the nginx image.
  - **Command:**
    ```bash
    podman image inspect nginx
    ```
  - **Explanation:** This command provides a detailed description of the nginx image including its layers and configuration.

---


**7. Create a container from the nginx image, run it in the background, and map it to host port 80.**
- **Solution:** Start an nginx container in detached mode and map port 80.
  - **Command:**
    ```bash
    podman run -d -p 80:80 nginx
    ```
  - **Explanation:** `-d` runs the container in the background; `-p 80:80` maps port 80 from the container to port 80 on the host.

---


**8. Create another instance of the nginx container, run it in the background, and map it to host port 8080.**
- **Solution:** Run another nginx container and map it to a different port.
  - **Command:**
    ```bash
    podman run -d -p 8080:80 --name web8080 nginx
    ```
  - **Explanation:** This configuration uses an unprivileged port, reducing the likelihood of port conflicts.

---


**9. List running containers again.**
- **Solution:** List all containers to verify both instances are running.
  - **Command:**
    ```bash
    podman ps
    ```

---


**10. Stop the first container created.**
- **Solution:** Stop the nginx container that was mapped to port 80.
  - **Command:**
    ```bash
    podman stop [container ID]
    ```
  - **Explanation:** Replace `[container ID]` with the actual container ID obtained from `podman ps`.

---


**11. Attempt to create another container instance named web8080.**
- **Solution:** Try creating a container with a name that's already in use.
  - **Explanation:** Podman will prevent using the same name for more than one container unless the original is removed.

---


**12. Inspect details of the web8080 container.**
- **Solution:** Obtain detailed configuration and state information of the web8080 container.
  - **Command:**
    ```bash
    podman inspect web8080
    ```

---


**13. List all downloaded images using Podman.**
- **Solution:** Display all container images that have been downloaded to your machine.
  - **Command:**
    ```bash
    podman images
    ```

---


**14. Export the nginx image.**
- **Solution:** Save the nginx image to a file.
  - **Command:**
    ```bash
    podman image save nginx -o /path/to/save/nginx-image.tar
    ```
  - **Explanation:** This command saves the entire nginx image including all its layers to a tar file.

---


**15. Manually modify and save a new container image.**
- **Solution:** Commit changes made within a container to create a new image.
  - **Command:**
    ```bash
    podman commit [container-id] [new-image-name]
    ```

---


**16. Modify the default web page of the web8080 container without terminating it.**
- **Solution:** Change the

content of the default web page in the running nginx container.
- **Command:**
  ```bash
  podman exec web8080 /bin/sh -c 'echo "Hello, World!" > /usr/share/nginx/html/index.html'
  ```

---


**17. Answer the following questions:**
- **a. Do containers lose their state when they are terminated?**
  - **Answer:** Yes, unless data is stored in persistent storage, it will be lost upon container termination.
- **b. Is it necessary to pull the container image before creating a container?**
  - **Answer:** Yes, unless the image is already available locally, it must be pulled from a registry.
- **c. Which command is used to import a Podman image?**
  - **Answer:** Use `podman load -i /path/to/image.tar`.
- **d. Does Podman support restarting containers?**
  - **Answer:** Yes, `podman restart [container-name or ID]`.

### Additional Reading
- [Podman Commands Documentation](https://docs.podman.io/en/v4.4/Commands.html)