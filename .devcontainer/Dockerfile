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



RUN git clone -b master https://github.com/flutter/flutter.git  /opt/flutter
RUN /opt/flutter/bin/flutter doctor
RUN /opt/flutter/bin/flutter upgrade-packages


ENV PATH="/opt/flutter/bin:$PATH"
ENV CMAKE_MAKE_PROGRAM=/usr/bin/ninja-build

# Install Android SDK
RUN wget -q https://dl.google.com/android/repository/commandlinetools-linux-7583922_latest.zip -O /tmp/android-sdk.zip \
    && unzip -qq /tmp/android-sdk.zip -d /opt/android-sdk \
    && rm /tmp/android-sdk.zip


# Set up Android SDK path
ENV ANDROID_SDK_ROOT=/opt/android-sdk
ENV PATH="${ANDROID_SDK_ROOT}/cmdline-tools/tools/bin:${ANDROID_SDK_ROOT}/platform-tools:${PATH}"

#Set up working directory to /app
WORKDIR /app


COPY . .


# Permissions
RUN sudo chown -R $(id -u):$(id -g) /opt/flutter/bin/cache
RUN sudo chown -R $(id -u):$(id -g) /opt/flutter/bin/cache/.dartignore

RUN export CMAKE_MAKE_PROGRAM=/usr/bin/ninja-build




EXPOSE 8080
# Starting the shell
CMD ["flutter", "run", "-d", "chrome"]
