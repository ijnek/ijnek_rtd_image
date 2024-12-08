FROM ubuntu:noble

# Disable interactive frontend
# NOTE: for this to take effect when using "sudo" apt install, we need the -E flag to preserve the environment variable inside the sudo command
ARG DEBIAN_FRONTEND=noninteractive

# Add sudo support for the non-root user
ARG USERNAME=ubuntu
RUN apt-get update && \
    apt-get install -y sudo && \
    echo "$USERNAME ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME

# Switch from root to user
USER $USERNAME

# Change directory to user home
WORKDIR /home/$USERNAME

# Install necesary packages
RUN sudo -E apt install -y git python3-sphinx-rtd-theme python3-pip

# Set locale to UTF-8
RUN sudo -E apt install -y locales && \
    sudo -E locale-gen en_US.UTF-8 && \
    sudo -E dpkg-reconfigure locales
