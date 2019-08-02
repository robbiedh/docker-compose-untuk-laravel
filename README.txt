cara menjalankan laravel di docker hanya dengan php, mysql dan phpmyadmin
1. lakukan git pull 

2. lalu jalankan  docker-compose up pastikan, terkoneksin dengan internet 
 dan jangan diclose terminalnya

3. pastikan  php_edc, mysql_ed,  dan phpmyadmin berjalan degan koment 
docker ps,maka akan tertampil 3 container degan  
nama  php_edc, mysql_ed,  dan phpmyadmin

4. setelah melakukan docker-compose up amak terdapat  folder dimana anda 
menaruh dockerFile dan docker-compose.yml , foldernya data-mysql,
data-php, data-workspace,

5. pindah project laravel masuk ke folder data-workspace 

6.  jika sudah  maka kita masuk ke bash  container  php dengan cara
docker exec  -it  <cotainer_id>  /bin/sh 
untuk container_id didaptkan dari docker ps 

7. masuk ke directory  dengan cara cd /var/www/dir_project pastikan folder project di main os
sudah terbaca di  container php

8. seperti biasa install terlebih dahulu dengan cara composer install untuk install 
lib2 yang dibutuhkan, dan jangan lupa php artisan key:generate generate key 
  
9. setelah itu configure database laravel (DB_HOST tidak menggunakan ip tetapi menggunakna
nama service dari docker-compose,jika nggak bisa terkoneksi pastikan phpmyadmin terkonesi,
jika ngga bisa terkoneksi  pastikan  container mysql udah jalan)
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=root
DB_USERNAME=root
DB_PASSWORD=root

10 lalu jalanakna dengan cara  
php artisan serve --host 0.0.0.0 --port 9000

12. buka browser  http://localhost:9000


