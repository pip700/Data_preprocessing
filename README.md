# Data_preprocessing

### Step 1: Allow Docker to use display

xhost +local:docker

### Step 2: RUN application via Docker

sudo docker run -d --rm \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v $(pwd):/workspace \
    ghcr.io/pip700/tkinter-app
