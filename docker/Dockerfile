FROM ubuntu:latest

WORKDIR /tools

RUN apt-get update && \
    apt-get install -y \
    wget \
    unzip \
    apt-transport-https \
    ca-certificates gnupg \
    curl && \
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    rm awscliv2.zip && \
    ./aws/install && \
    echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - && \
    curl -sL https://aka.ms/InstallAzureCLIDeb | bash && \
    apt-get update && \
    apt-get install -y google-cloud-sdk && \

RUN wget https://releases.hashicorp.com/terraform/0.12.21/terraform_0.12.21_linux_amd64.zip -O terraform.zip && \
    unzip terraform.zip -d /usr/bin

CMD [ "/bin/bash" ]