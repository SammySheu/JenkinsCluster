FROM jenkins/ssh-agent

USER root

# 安裝 Docker 的依賴項
RUN apt-get update && \
    apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    sudo \
    software-properties-common \
    lsb-release

# 添加 Docker 的 GPG key
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# 設置 Docker 倉庫
RUN echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

# 安裝 Docker CLI
RUN apt-get update && \
    apt-get install -y docker-ce-cli

# 創建 docker 群組（如果需要）
RUN groupadd -f docker && usermod -aG docker jenkins
    
USER jenkins