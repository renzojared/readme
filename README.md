# DOCKER CONTAINER
>Usado para sintaxis de servidores en docker

Visita la documentación oficial,[^1] o la guía de markdown.[^2]

## General
Remover contenedores e imágenes:
```Shell
docker ps -a
docker images
docker rm <ID CONTAINER>
docker rmi c6b70534b534 <ID IMAGEN>
```
Docker compose: 
```Shell
docker inspect <CONTAINER_ID>
```

## SQL SERVER

<details><summary>Run container</summary>
<p>

```Shell
docker pull mcr.microsoft.com/mssql/server:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=docker@UPC09"-e "MSSQL_PID=Express"  -p 1433:1433 --name sql-server --hostname dbsql -d mcr.microsoft.com/mssql/server:2017-latest
```

</p>
</details>

## MYSQL SERVER

<details><summary>Run container</summary>
<p>

```Shell
docker pull mysql
docker run --name mysql-server -e MYSQL_ROOT_PASSWORD=docker@UPC -p 3306:3306 -d mysql:latest
```

> Optional: 
> ```
> docker run --name mysql -h hostmysql -u root -e MYSQL_ROOT_PASSWORD=docker@SD -d mysql -p 3366:3306 --protocol=tcp 
> ```


</p>
</details>

<details><summary>Export database in dbeaver</summary>
<p>

| Description | Command |
| --- | --- |
| 1. Connect to the bash | `docker exec -it CONTAINER_ID bash`  |
| 2. Login like root | `mysql --user=root --password`|
| 3. Chante to native password | `ALTER USER 'username' IDENTIFIED WITH mysql_native_password BY 'password';`|

Try export the dump database
</p>
</details>

## POSTGRES SERVER

<details><summary>Run container</summary>
<p>

```Shell
docker pull postgres
docker run --name postgresql-server -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres
```

</p>
</details>

<details><summary>Copy file from Windows</summary>
<p>

```Shell
docker exec -i -t <CONTAINER_ID> /bin/bash
cd home
mkdir micv
exit
docker cp C:\Users\rleon\Documents\repo\own\TPA.General\MICV\dump\micv_prod_27042022.sql micv-postgres:/home/micv/
```

</p>
</details>

<details><summary>Restore database</summary>
<p>

```Shell
root: psql -U postgres --quiet -W -h localhost micv_prod < micv_prod_15072021.sql
```

</p>
</details>

<details><summary>Extra commands</summary>
<p>

```Shell
\conninfo
\q
\c micv_prod
```

</p>
</details>

[^1]: [Writing on Github](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github)
[^2]: [Markdown guide](https://www.markdownguide.org/getting-started/)