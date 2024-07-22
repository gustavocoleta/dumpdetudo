# Dump de Tudo

## Iniciar o container
    
```bash
docker-compose up
```

## Restaurar o dump

Adicione o arquivo `dumpdetudo.sql` na pasta `.backup` e execute o comando abaixo.

```bash
docker exec dumpdetudo restore
```

Caso o arquivo tenha outro nome, adicione-o na pasta `.backup` execute o comando:

```bash
docker exec dumpdetudo restore [NAME_OF_THE_BACKUP_FILE.sql]
```

⚠️ Ao executar o comando acima, TODOS os bancos de dados serão apagado e substituídos pelo dump.