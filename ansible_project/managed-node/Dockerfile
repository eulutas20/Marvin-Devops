FROM python:3.9-slim
# Temel paketlerin kurulumu
RUN apt-get update && \
    apt-get install -y python3 openssh-server && \
    mkdir /var/run/sshd

# Gerekli dizinlerin oluşturulması
RUN mkdir -p /root/.ssh && mkdir /var/run/sshd

# SSH anahtarlarının kopyalanması
COPY id_rsa.pub /root/.ssh/authorized_keys

# SSH anahtar izinlerinin ayarlanması
RUN chmod 600 /root/.ssh/authorized_keys

# Portların açılması
EXPOSE 22 80

# SSH sunucusunun çalışması
CMD ["/usr/sbin/sshd", "-D"]