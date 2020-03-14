# Geração Karol Wojtyla - Docker

Copie o bloco de código abaixo e cole num terminal dentro de sua pasta de jobs

```shell
echo -e "\033[1;92m 1 - Clonando repositório com recurse-submodules...\033[m" &&\
git clone git@github.com:geracaokw/geracaokw-docker.git --recurse-submodules &&\
echo -e "\033[1;92m 2 - Entrando na pasta do repositório clonado...\033[m" &&\
cd geracaokw-docker &&\
echo -e "\033[1;92m 3 - Entrando na pasta docker...\033[m" &&\
cd docker &&\
echo -e "\033[1;92m 4 - Buildando o docker...\033[m" &&\
docker-compose build &&\
echo -e -e "\033[1;92m 5 - Parando possíveis dockers abertos...\033[m" &&\
dockerstop &&\
echo -e "\033[1;92m 6 - Ligando o docker...\033[m" &&\
dockerup &&\
echo -e "\033[1;92m 7 - Aguardando banco de dados...\033[m" &&\
while ! docker-compose exec mysql mysqladmin --user=root --password=root --host "127.0.0.1" ping --silent &> /dev/null ; do
    echo "Waiting for database connection..."
    sleep 2
done
echo -e "\033[1;92m Acesse http://localhost\033[m"
python -m webbrowser "http://localhost" > /dev/null 2>&1
```
