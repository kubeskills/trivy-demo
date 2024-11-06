# Using Trivy to Detect Vulnerabilities

A demo comparing a minimal Docker image with a large one. This will include building the images, scanning them, and highlighting differences in terms of vulnerabilities and package counts.

## Pre-requisites
- Docker
- Trivy

### STEP 1: Create Two Dockerfiles - Minimal and Large

[Minimal Dockerfile](Dockerfile.minimal)

[Large Dockerfile](Dockerfile.large)

### STEP 2: Build the Docker Images

```bash
# Build minimal image
docker build -t demo:minimal -f Dockerfile.minimal .

# Build large image
docker build -t demo:large -f Dockerfile.large .

```

The output should look like the following:
```bash
$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED              SIZE
demo          large     d7fb884ead04   About a minute ago   572MB
demo          minimal   6eeb4f7cccce   20 hours ago         7.79MB
hello-world   latest    d2c94e258dcb   18 months ago        13.3kB
```


### STEP 3: Scan both Images and Save the Results

```bash
# Scan minimal image and save output
trivy image demo:minimal > minimal_scan_report.txt

# Scan large image and save output
trivy image demo:large > large_scan_report.txt
```

View Scan Reports Here:  
[Minimal Scan Report](minimal-scan-report.txt)  
[Large Scan Report](large-scan-report.txt)

