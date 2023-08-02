FROM ubuntu:18.04

ENV TZ=America/Bogota \
    DEBIAN_FRONTEND=noninteractive

WORKDIR /var/www/html

# Actualizar nuevamente los repositorios y luego instalar PHP 7.4 y las extensiones
RUN apt-get update && apt-get upgrade && apt-get install -y \
    php \
    php-mysql \
    php-curl \
    php-gd \
    php-mbstring \
    php-xml \
    php-xmlrpc \
    php-soap \
    php-intl \
    php-zip \
    php-cli \
    php-ldap \
    php-redis \
    php-imagick \
    php-pear \
    php-xdebug \
    curl \
    git \
    libssl1.0-dev \
    nodejs-dev \
    node-gyp \
    nodejs \
    npm \
    golang \
    mysql-server \
    mysql-client

#RUN npm install -g @angular/cli@9.0.4

RUN useradd -m john

RUN export GOPATH=$HOME/go \
    export PATH=$PATH:$GOPATH/bin:/usr/local/go/bin

RUN chown -R john:john /var/www/html

RUN apt-get install -y openjdk-8-jre

RUN apt-get install -y openjdk-8-jdk

RUN update-alternatives --config java

# Instalar wget
RUN apt-get update && apt-get install -y wget

# USER root

# # Descargar y agregar la clave GPG de Jenkins al keyring
# RUN curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | gpg --dearmor -o /tmp/jenkins-keyring.gpg

# # Mueve la clave GPG al directorio /usr/share/keyrings/
# RUN mv /tmp/jenkins-keyring.gpg /usr/share/keyrings/jenkins-keyring.gpg

# # Cambia los permisos del archivo a fin de que el usuario pueda leerlo
# RUN chmod 644 /usr/share/keyrings/jenkins-keyring.gpg

# # Agregar el repositorio de Jenkins al archivo sources.list.d utilizando la clave del keyring
# RUN echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.gpg] https://pkg.jenkins.io/debian binary/" > /etc/apt/sources.list.d/jenkins.list

# # Instalar Jenkins
# RUN apt-get update && apt-get install -y jenkins

# Instalar Composer globalmente
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

VOLUME [ "/var/www/html", "/home/john" ]

EXPOSE 8000

USER john

ENTRYPOINT [ "php", "-S", "0.0.0.0:8000" ]