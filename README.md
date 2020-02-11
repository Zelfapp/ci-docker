# CodeIgniter (CI) Development Environment

#### Docker env: nginx, php-fpm 7.3

#### CI (located in /app):

- CI Test Site [http://cidocker.local](http://cidocker.local)

### Step 1 - Clone cidocker repo

```
https://github.com/Zelfapp/ci-docker.git
```

### Step 2 - Add site to /etc/hosts

```
sudo "127.0.0.1\tcidocker.local" >> /etc/hosts
```

### Step 3 - docker-compose up

From the repository root run the following command. Tested on ubuntu linux only.

This will dynamically pass in user/group id's and your machine's ip address required for
permissions and debugging. (Change 192.168.1.12 to your actual ipv4 address.)

```
userid=$(id -u) groupid=$(id -g) ipaddr=192.168.1.12 docker-compose up --build
```

### Note: nginx/php-fpm configuration files are located in /server.
