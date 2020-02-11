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
permissions and debugging.

```
userid=$(id -u) groupid=$(id -g) ipaddr=$(ip route get 8.8.8.8 | awk '{print $NF; exit}') docker-compose up --build
```

### Step 4 - navigate to CI Test Site in browser. 

While the script will process quickly to display the welcome message. If you open your console ->
network tab you'll see that while the php script processed in < .00 ms the page takes > 400 ms to
display. **This is a very simple php script with zero processing occurring. It should load in less
than < 35 ms. On bare metal (no docker), it loads in < 10 ms.**

Something is incorrectly configured in docker-compose or in some conf file.

## PHP script process time (0.0021 ms).

![Welcome page](https://mrkr.io/s/5e421fa099ee9d2163acd13f/0)

## Actual browser load time (418 ms).

![Load time in browser](http://i.imgur.com/rD0DM2J.png)

### Note: nginx/php-fpm configuration files are located in /server.
