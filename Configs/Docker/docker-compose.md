services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: laravel_app
    volumes:
      - .:/var/www/my_laravel_app
      - /mnt/usb:/mnt/usb
    restart: unless-stopped

  nginx:
    image: nginx:latest
    container_name: laravel_nginx
    ports:
      - "80:80"
    volumes:
      - .:/var/www/my_laravel_app
      - ./docker/nginx/default.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - app
    restart: unless-stopped
