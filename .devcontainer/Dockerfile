# Base: MATLAB Runtime 2025b
FROM containers.mathworks.com/matlab-runtime:r2025b

# System deps + git
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    curl bzip2 ca-certificates git && \
    rm -rf /var/lib/apt/lists/*

# Install micromamba (provides `mamba`)
ENV MAMBA_ROOT_PREFIX=/opt/micromamba
RUN curl -L https://micro.mamba.pm/api/micromamba/linux-64/latest -o /tmp/micromamba.tar.bz2 && \
    mkdir -p /tmp/micromamba && \
    tar -xjf /tmp/micromamba.tar.bz2 -C /tmp/micromamba && \
    mv /tmp/micromamba/bin/micromamba /usr/local/bin/micromamba && \
    rm -rf /tmp/micromamba /tmp/micromamba.tar.bz2

# Create conda env and install python, ipykernel, pip
RUN micromamba create -y -n bluemath -c conda-forge python=3.11 pip bluemath-tk ipykernel && \
    micromamba clean -a -y

# Auto-activate env for interactive shells
SHELL ["bash", "-lc"]
ENV SHELL=/bin/bash
RUN echo 'eval "$(micromamba shell hook -s bash)" && micromamba activate bluemath' >> /etc/bash.bashrc

