FROM ubuntu:latest

# I update package lists and install necessary dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip openssh-client ansible && \
    apt-get clean

# I create the .ssh directory and set up SSH keys
# The private key (id_rsa) and public key (id_rsa.pub) are copied to /root/.ssh/
RUN mkdir /root/.ssh
COPY ansible/id_rsa /root/.ssh/id_rsa
COPY ansible/id_rsa.pub /root/.ssh/id_rsa.pub
RUN chmod 600 /root/.ssh/id_rsa /root/.ssh/id_rsa.pub

# I copy Ansible configuration files
# The ansible.cfg file is copied to /etc/ansible/
# The inventory file is copied to /etc/ansible/hosts
# The playbook.yml file is copied to /etc/ansible/
COPY ansible/ansible.cfg /etc/ansible/ansible.cfg
COPY ansible/inventory /etc/ansible/hosts
COPY ansible/playbook.yml /etc/ansible/playbook.yml

# I install and configure the SSH server
# The SSH server is installed and configured to allow root loginn
RUN apt-get install -y openssh-server && \
    mkdir /var/run/sshd && \
    echo 'root:password' | chpasswd && \
    sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# I expose port 22 for SSH access
EXPOSE 22

# I start the SSH server
CMD ["/usr/sbin/sshd", "-D"]
