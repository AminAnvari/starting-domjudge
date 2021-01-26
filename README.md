# Starting DOMjudge
A simple guide for starting [DOMjudge](http://domjudge.org) using some helper Bash scripts

## Initialization

1. Clone this repository.
2. ```chmod +x *.sh```

## Start server

1. ```sudo ./config_user_and_grub.sh```
2. Restart your computer.
3. You can modify *MARIADB_VERSION* and *DOMJUDGE_VERSION* variables in *config_docker.sh* file (according to the latest released versions). Also, you can leave them unchanged.
4. ```./config_docker.sh```
5. You can modify *MYSQL_PASSWORD* and *MYSQL_ROOT_PASSWORD* variables in *start_server.sh* file (according to your own arbitrary choices). Also, you can leave them unchanged.
6. ```./start_server.sh```
7. Check [http://localhost:12345](http://localhost:12345) via your Web browser. You should see DOMjudge now!

## Start workers

Suppose there is a working server on a machine. It doesn't matter the worker and the server are on the same machine or not; you should start a server beside the worker.

1. ```./config_user_and_grub.sh```
2. Restart your computer.
3. You can modify *MARIADB_VERSION* and *DOMJUDGE_VERSION* variables in *config_docker.sh* file (according to the latest released versions). Also, you can leave them unchanged.
4. ```./config_docker.sh```
5. You can modify *MYSQL_PASSWORD* and *MYSQL_ROOT_PASSWORD* variables in *start_server.sh* file (according to your own arbitrary choices). Also, you can leave them unchanged.
6. ```./start_server.sh```
7. Modify *SERVER_URL* and *WORKER_PASSWORD* variables in *start_server.sh* file. The first one should be set to the URL of DOMjudge server, but the second one can have an arbitrary value.
8. ```./start_worker.sh 0```
9. Now, a single worker (with ID 0) is up. You can start more concurrent workers on the same machine. For the next workers, just use ```./start_worker.sh 1```, ```./start_worker.sh 2``` and so on. The maximum number of workers equals the number of your machine CPU cores.

## See also

- [domjudge/domserver - Docker Hub](https://hub.docker.com/r/domjudge/domserver)
- [domjudge/judgehost - Docker Hub](https://hub.docker.com/r/domjudge/judgehost)

