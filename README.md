# Instalación de WordPress en Ubuntu Server

---

## 1. Actualizar paquetes del sistema
Ejecuta el siguiente comando para actualizar los paquetes de tu sistema operativo:

```bash
sudo apt update
```
Deberías obtener una salida similar a esta:

<img width="1176" height="560" alt="image" src="https://github.com/user-attachments/assets/ec6923b9-9374-4454-8d9f-a422f1fe67a7" />

---

### Instalar Apache, PHP y MySQL
Instala los paquetes necesarios con el siguiente comando:

```bash
sudo apt install apache2 \
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
                 php-zip
```
De esta forma:

<img width="897" height="291" alt="image" src="https://github.com/user-attachments/assets/1e73b9f4-e3d7-421d-9b6e-96e49d3ca9ab" />


### Instalar WordPress
Descarga e instala WordPress:

<img width="1168" height="291" alt="image" src="https://github.com/user-attachments/assets/5dd39336-20c8-4a01-846c-33c695daef3c" />

---

## 2. Configurar WordPress en Apache 
Abre el archivo de configuración de WordPress en Apache:

```bash
sudo nano /etc/apache2/sites-available/wordpress.conf
```

apache
```bash
<VirtualHost *:80>
    ServerName hostname.example.com
    DocumentRoot /srv/www/wordpress

    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>

    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
```
<img width="1068" height="492" alt="image" src="https://github.com/user-attachments/assets/80316e6e-c461-4258-be97-ab2715da10ba" />


Activar la configuración y reiniciar Apache
```bash
sudo a2ensite wordpress
sudo a2enmod rewrite
sudo systemctl reload apache2
```
Salida esperada:
<img width="1055" height="277" alt="image" src="https://github.com/user-attachments/assets/833b1c1e-b692-4050-b301-7b975e4fec8d" />

---

## 3. Crear la base de datos para WordPress 
Entrar en MySQL
```bash
sudo mysql -u root
```
<img width="1021" height="291" alt="Captura desde 2025-09-26 13-34-43" src="https://github.com/user-attachments/assets/47532fb0-ab82-4406-af35-ec458f0a697e" />


Crear la base de datos y usuario
```bash
create database wordpress;
create user wordpress@localhost idenfitied by 'TU_CONTRASEÑA';
grant select, insert, update, delete, create, drop, alter on wordpress.* to wordpress@localhost;
flush privileges;
exit;
```
<img width="871" height="250" alt="Captura desde 2025-09-26 13-41-18" src="https://github.com/user-attachments/assets/05362fc1-ada2-4ff1-951b-e5f347fbe3f1" />


---

## 4. Configurar WordPress para conectarse a la base de datos 
Primero, copie el archivo de configuración de ejemplo a wp-config.php:

```bash
sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
```
Ahora hay que configurar las credenciales de la base de datos en el archivo de configuración
```bash
sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/password_here/TU_CONTRASEÑA/' /srv/www/wordpress/wp-config.php
```
<img width="1168" height="203" alt="Captura desde 2025-09-26 13-56-54" src="https://github.com/user-attachments/assets/9fe2a2c1-2195-4286-a395-82ba97e89f02" />

---

Luego tenemos que modificar las siguientes líneas para que coincidan con tu base de datos:
```bash
sudo -u www-data nano /srv/www/wordpress/wp-config.php
```
<img width="570" height="160" alt="config" src="https://github.com/user-attachments/assets/3aace8ad-8bf2-44b6-a434-d5361ae964cc" />

Generar claves de seguridad 
Visita el siguiente enlace para generar las claves secretas de WordPress:  
https://api.wordpress.org/secret-key/1.1/salt/

Copia las claves generadas y pégalas en el archivo wp-config.php:

<img width="1148" height="319" alt="image" src="https://github.com/user-attachments/assets/e0f6ad20-f0f9-47c7-b1b0-39666342aad4" />

---

## 6. Comprobación 
Para la comprobación abrimos el navegador y buscamos la ip de nuestro servidor, seleccionamos el idioma y completamos estos campos:
<img width="1182" height="933" alt="image" src="https://github.com/user-attachments/assets/ac83df61-c3b6-4dd9-b4ab-0d001269c225" />  

Una vez finalizado esto le damos a instalar wordpress y se nos abre la siguiente ventana en la cual introduciremos el nombre de usuario / correo electronico y su contraseña:  

<img width="1162" height="565" alt="image" src="https://github.com/user-attachments/assets/52b5cba9-012c-44c4-b532-00764b826cfe" />  

Y aquí podemos observar que el inicio de sesion fue correcto:  

<img width="1189" height="941" alt="image" src="https://github.com/user-attachments/assets/0e4bdf7e-52f9-4ad5-a494-65c91c563d21" />



