#php ใช้ version 7.1 สามารถเปลี่ยนได้ตามที่เราต้องการแต่ต้องเป็นตัว fpm นะครับ เพื่อที่จะให้กับ nginx
FROM php:7.4-fpm 

#Install คำสั่งสำหรับการลง package ที่ laravel required ไว้นะครับ
# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

#RUN docker-php-ext-configure \
#  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# ตามด้วยคำสั่งสำหรับการลง php extension ครับ
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# อันนี้ลงเพิ่มเติมคือ composer นั้นเอง เป็นตัว package manager สำหรับการจัดการพวก dependency ของภาษา php ครับ
RUN curl -sS https://getcomposer.org/installer | \
  php -- --install-dir=/usr/local/bin --filename=composer