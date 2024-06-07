# control-node/Dockerfile
FROM ubuntu:latest

# Temel paketlerin kurulumu
RUN apt-get update && \
    apt-get install -y python3 python3-pip openssh-client && \
    pip3 install ansible

# Ansible dosyalarının kopyalanması
COPY ansible/ /etc/ansible/

# SSH anahtarlarının kopyalanması
COPY id_rsa /root/.ssh/id_rsa
COPY id_rsa.pub /root/.ssh/id_rsa.pub

# SSH anahtar izinlerinin ayarlanması
RUN chmod 600 /root/.ssh/id_rsa && chmod 644 /root/.ssh/id_rsa.pub

# Çalışma dizininin ayarlanması
WORKDIR /etc/ansible

# Anahtarların ve ansible dosyalarının sahipliğinin root olarak ayarlanması
RUN chown -R root:root /etc/ansible && chown -R root:root /root/.ssh

# Ansible'ın çalışabilmesi için shell'in açık tutulması
CMD ["/bin/bash"]
