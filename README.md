# Projeto magento 2.4 base.

Utilize este repositorio para iniciar um projeto Magento 2.4

1- Clone o repositório

2- Prepare as variáveis de ambiente

```cp sample.env .env```

3- Faça o download e descompacte a versão do magento desejada dentro da pasta www, de modo que o index.php fique na raiz: ```www/index.php```

4- Adicione a linha ```127.0.0.1 magento2.local``` em ```/etc/hosts```

5- Execute o docker

```docker-compose -d --build```

6- Acesse o container

```bin/container```

7- Dê permissão de escrita nas pastas e no CLI do magento

```shell script
chmod -R 0777 pub
chmod -R 0777 var
chmod -R 0777 generated
chmod -R 0777 app/etc
chmod u+x bin/magento
```

8- Atualize o magento usando o composer (opcional)

```composer update```

9 - Execute o comando de instalação do magento

```shell script
bin/magento setup:install \
--base-url=http://magento2.local/ \
--db-host=mysql \
--db-name=magento2 \
--db-user=root \
--db-password=tiger \
--admin-firstname=Eliel \
--admin-lastname=dePaula \
--admin-email=elieldepaula@gmail.com \
--admin-user=elieldepaula \
--admin-password=123mudar \
--language=pt_BR \
--currency=BRL \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=elasticsearch6 \
--elasticsearch-host=elasticsearch \
--elasticsearch-password=elastic
```

## Dicas

Instalação por linha de comando



Desabildar a autenticação de 2 fatores:
```shell script
bin/magento module:disable Magento_TwoFactorAuth
bin/magento cache:flush
```