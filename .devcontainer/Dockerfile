FROM mcr.microsoft.com/devcontainers/base:jammy


#Install necc. dependacies
RUN sudo apt-get update && apt-get install -y \
    git \
    curl \
    unzip \
    wget \
    zlib1g-dev \
    libffi-dev \
    libssl-dev \
    libelf-dev \
    libncurses5-dev \
    libgtk-3-dev \
    build-essential \
    python3 \
    python3-pip \
    ninja-build \
    cmake \
    clang \
    pkg-config




# Install Flutter and Dart


RUN git clone https://github.com/flutter/flutter.git /opt/flutter
RUN /opt/flutter/bin/flutter doctor




ENV PATH="/opt/flutter/bin:$PATH"
ENV CMAKE_MAKE_PROGRAM=/usr/bin/ninja-build


#Set up working directory to /app
WORKDIR /app


COPY . .


# Permissions
RUN sudo chown -R $(id -u):$(id -g) /opt/flutter/bin/cache
RUN sudo chown -R $(id -u):$(id -g) /opt/flutter/bin/cache/.dartignore

RUN export CMAKE_MAKE_PROGRAM=/usr/bin/ninja-build

# Starting the shell
CMD ["flutter", "run", "-d", "chrome"]
