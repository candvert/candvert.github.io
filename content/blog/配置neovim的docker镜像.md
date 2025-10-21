---
title: 配置neovim的docker镜像
description: 配置neovim的docker镜像
date: 2025-10-21
lastmod: 2025-10-21
tags:
  - neovim
  - docker
---
~/.bashrc 文件

~/.config/nvim 文件

~/.local/share/nvim 文件夹

安装 git、curl 或 GNU wget、unzip、GNU tar（tar 或 gtar）、gzip

安装gcc编译器

## Dockfile
```sh
FROM ubuntu:22.04

# 1. 安装系统依赖（这些是不常变化的部分）
RUN apt update && \
    apt install -y --no-install-recommends \
    gcc \
    git \
    wget \
    unzip \
    tar \
    gzip \
    python3 \
    python3-venv && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*

# 2. 创建应用程序用户
RUN useradd -m -s /bin/bash cand

# 3. 设置工作目录并提前创建必要的目录结构
WORKDIR /home/cand
RUN mkdir -p /home/cand/.config /home/cand/.local/share && \
    chown -R cand:cand /home/cand

# 4. 复制文件并直接设置所有者（以root身份，确保有权限）
COPY --chown=cand:cand ./Dockerfile ./Dockerfile
COPY --chown=cand:cand ./nvim ./nvim
COPY --chown=cand:cand ./.config/nvim ./.config/nvim
COPY --chown=cand:cand ./.local/share/nvim ./.local/share/nvim
COPY --chown=cand:cand ./.bashrc ./.bashrc
COPY --chown=cand:cand ./program_lang ./program_lang

# 5. 切换到非特权用户
USER cand

# 6. 设置默认命令
CMD ["/bin/bash"]
```