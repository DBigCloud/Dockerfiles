FROM centos

# Creamos el grupo y el usuario monogodb.
RUN groupadd -r mongodb && useradd -mrg mongodb mongodb

# Copiamos el repositorio de MongoDB 3.0 en la ruta indicada.
ADD mongodb-org-3.0.repo /etc/yum.repos.d/mongodb-org-3.0.repo

# Procedemos a instalar MongoDB.
RUN yum install -y mongodb-org
RUN yum clean all

# Creamos la carpeta en la que va a correr el contenedor y establecemos los permisos para el usuario mongodb
RUN mkdir -p /data/db && chown -R mongodb:mongodb /data/db

# Establecemos la carpeta creada enteriormente como el volumen
VOLUME /data/db

# Ruta del home del usuario mongodb
ENV HOME /home/mongodb

# Usuario que va a ejecutar el contenedor
USER mongodb

# Puerto por defecto por el que escuchará el contenedor.
EXPOSE 27017

# La ejecucción de MongoDB
CMD ["mongod"]
