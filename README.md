# Create network
docker network create laranet


## #### Build Stage #### ##

# Build nginx image
docker build -t nginx nginx -- if you are inside nginx folder, change 'nginx' to '.'
docker build -t nginx nginx -f nginx/Dockerfile.prod

# Build laravel image
docker build -t laravel laravel -- if you are inside laravel folder, change 'laravel' to '.'
docker build -t laravel laravel -f laravel/Dockerfile.prod

#### ### ## ## ## ## ####


## #### Run Stage #### ##

# Run nginx
dodkcer run -d --network laravel-nginx --name nginx nginx-laravel

# Run laravel
dodkcer run -d --network laravel-nginx --name laravel laravel

#### ### ## ## ## ## ####