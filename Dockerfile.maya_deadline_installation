# Use base image compatible for linux + both Maya and Dealine installers
FROM ubuntu:20.04

# Set Env variable for non-interactive installations
ENV DEBIAN_FRONTEND = non-interactive

# Get packages for the installation of Maya and Deadline
RUN apt-get update && apt-get install -y \
    wget \
    python3 \
    sudo \ 
    libx11-6 \
    libgl1-mesa-glx \
    libgl1ul-mesa \
    # remove additional unnecessary packages in the dockerfile
    && rm -rf /var/lib/apt/lists/*

# -- INSTALL DEADLINE ON LOCAL MACHINE --
COPY Deadline-10.4.0.10-linux-installers.tar /tmp/DeadlineInstaller.tar
RUN tar -xf /tmp/DeadlineInstaller.tar -C /tmp && \
    # install repo
    /tmp/DeadlineInstaller/install --mode unattended --installClient && \
    # install client
    # install AWS portal?
    rm -rf /tmp/DeadlineInstaller /tmp/DeadlineInstaller.tar

# Set deadline path for commands

# -- INSTALL MAYA ON LOCAL MACHINE -- 
COPY Autodesk_Maya_2025_3_ML_Linux_64bit.tgz /tmp/AutodeskMayaInstaller.tgz
RUN tar -xzf /tmp/AutodeskMayaInstaller.tgz -C /tmp && \
    ./install silent && \
    rm -rf /tmp/AutodeskMataInstaller.tgz /tmp/install

# Set Maya path for commands