# Instalacion_SGE
### Guía para instalar WordPress en Ubuntu Server

El primer paso sería ejecutar el comando ***sudo apt update*** para actualizar los paquetes del sistema operativo
Deberia de dar una salida similar a esta:

<img width="1176" height="560" alt="image" src="https://github.com/user-attachments/assets/ec6923b9-9374-4454-8d9f-a422f1fe67a7" />


Posteriormente procederíamos a instalar los paquetes necesarios para instalar **PHP** y **Apache** con el siguiente comando:

*sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip*
                 
De esta forma:
<img width="897" height="291" alt="image" src="https://github.com/user-attachments/assets/1e73b9f4-e3d7-421d-9b6e-96e49d3ca9ab" />


Instalar WordPress

<img width="1168" height="291" alt="image" src="https://github.com/user-attachments/assets/5dd39336-20c8-4a01-846c-33c695daef3c" />

Crear base datos:

<img width="1021" height="291" alt="image" src="https://github.com/user-attachments/assets/ed6194ef-a376-4029-869b-2e24aa674ad6" />

Ahora le asignaremos todos los permisos al usuario que vamos a crear:
<img width="871" height="250" alt="image" src="https://github.com/user-attachments/assets/2e5c4109-2b9a-4a7b-93c4-866f44c039c5" />

Configuracion wordpress para la conexion a la BD
<img width="1168" height="203" alt="image" src="https://github.com/user-attachments/assets/5eb05c1c-90ac-4f6e-9379-357885cd73b4" />

A continuacion usaremos este comando para abrir el siguiente fichero:
<img width="1169" height="57" alt="image" src="https://github.com/user-attachments/assets/3d88e4d2-8a1f-422e-b122-41b35cb9b2c3" />


Una vez abierto modificaremos estas lineas
<img width="570" height="160" alt="Captura desde 2025-09-26 14-01-38" src="https://github.com/user-attachments/assets/3aace8ad-8bf2-44b6-a434-d5361ae964cc" />


Para que queden asi:
<img width="1169" height="311" alt="image" src="https://github.com/user-attachments/assets/02fed258-ba40-4865-a1c6-9e76d663828a" />




