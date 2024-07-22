# Dump de Tudo

## Iniciar o container
    
```bash
docker-compose up
```

## Restaurar o dump

⚠️ Ao executar os comandos de restore, **TODOS** os bancos de dados serão apagado e substituídos pelo dump.

ℹ️ Caso não queira perder os dados já restaurados, renomeie a pasta `.data` para  qualquer nome que inicie com `.data`, exemplo `.data.bkp` antes de executar o comando de restore.

- ### Restaurar o dump padrão

    Adicione o arquivo `dumpdetudo.sql` na pasta `.backup` e execute o comando abaixo.

        ```bash
        docker exec dumpdetudo restore
        ```

- ### Restaurar um dump específico

    Caso o arquivo tenha outro nome, adicione-o na pasta `.backup` execute o comando:

    ```bash
    docker exec dumpdetudo restore [NAME_OF_THE_BACKUP_FILE.sql]
    ```

## Configuração nas API's

Para utilização do dump nas API's, é necessário alterar os environments de banco de dados, no arquivo `.env.development` de cada API, com os valores abaixo, e reiniciar os containers.

- VRMasterAPIRede
    ```env
    #POSTGRES
    DB_HOST='dumpdetudo'
    DB_USERNAME='postgres'
    DB_PASS='postgres'
    DB_DATABASE='rede'
    DB_PORT=54323
    ```
- VRMasterAPIRede
    ```env
    #POSTGRES
    DB_HOST='dumpdetudo'
    DB_USERNAME='postgres'
    DB_PASS='postgres'
    DB_DATABASE='usuario'
    DB_PORT=54323
    ```

## Configurar a Docker Network

A rede `vrmasterapi-net` deve ser criada antes de iniciar os containers, contudo se trata da mesma rede utilizada pelas API's, caso não tenha sido criada, execute o comando abaixo:

```bash 
docker network create vrmasterapi-net
```