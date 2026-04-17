
# 📦 Data Preprocessing (Dockerized Tkinter App)

## 🧩 Introduction

This project provides a Dockerized environment to run a Tkinter-based data preprocessing application. It allows GUI applications to run inside a Docker container by forwarding the display from the host system.

---

## 📚 Table of Contents

* [Introduction](#-introduction)
* [Prerequisites](#-prerequisites)
* [Installation](#-installation)
* [Usage](#-usage)
* [Features](#-features)
* [Configuration](#-configuration)
* [Troubleshooting](#-troubleshooting)
* [License](#-license)

---

## ⚙️ Prerequisites

Make sure you have the following installed:

* Docker
* Linux-based OS with X11 display server
* `xhost` utility

---

## 🛠 Installation

Clone your project (if applicable):

```bash
git clone <your-repository-url>
cd <your-project-directory>
```

---

## 🚀 Usage

### Step 1: Allow Docker to Access Display

```bash
xhost +local:docker
```

This command allows Docker containers to use your system's X server for GUI rendering.

---

### Step 2: Run the Application via Docker

```bash
sudo docker run -d --rm \
-e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v $(pwd):/workspace \
ghcr.io/pip700/tkinter-app:v2
```

#### Explanation:

* `-d`: Run container in detached mode
* `--rm`: Automatically remove container when it exits
* `-e DISPLAY=$DISPLAY`: Pass display environment variable
* `-v /tmp/.X11-unix:/tmp/.X11-unix`: Share X11 socket
* `-v $(pwd):/workspace`: Mount current directory into container
* `ghcr.io/pip700/tkinter-app:v2`: Docker image

---

## ✨ Features

* Run Tkinter GUI apps inside Docker
* Seamless display forwarding via X11
* No need to install dependencies locally
* Portable and reproducible environment

---

## ⚙️ Configuration

You can modify:

* Mounted directory (`$(pwd):/workspace`) for different data sources
* Docker image version (`v2`) for updates or compatibility
* DISPLAY variable if using remote sessions

---

## 🧪 Troubleshooting

### GUI Not Showing?

* Ensure `xhost +local:docker` is executed
* Verify `$DISPLAY` variable:

  ```bash
  echo $DISPLAY
  ```

### Permission Issues

* Try running Docker without `sudo` (if configured)
* Check X server permissions

### Wayland Users

* If you're using Wayland (e.g., Ubuntu newer versions), X11 forwarding may not work directly. Consider using XWayland or switching sessions.

---

## 📄 License

Specify your project license here (e.g., MIT, Apache 2.0).

---

## 🤝 Contributors

pip700


