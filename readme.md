# Laravel Alpine

Docker image built in 

- Nginx (+ FastCGI Cache)
- PHP FPM
- GIT
- Composer

Ready for Laravel, based on tiny Alpine image.

## Getting started

```
docker run -v $(pwd):/var/www/html -p 80:80 ferri/laravel-alpine
```

## Manual build

```
docker build -t ferri/laravel-alpine .
```