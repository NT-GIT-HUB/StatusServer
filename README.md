# StatusServer
__Parte 1 - Baixando Script__ 

```cd /root && wget https://raw.githubusercontent.com/NT-GIT-HUB/StatusServer/main/onlineapp.sh && chmod +x onlineapp.sh```


__Parte 2: Instalando Apache2 e Cron__

```apt install apache2 && apt install cron```

Ps:Se der erro na instalação do apache pode ser por causa da porta 80 rodando no sever,só parar e dar reboot na máquina,e instalar de novo;

__Parte 3: Configurando portas e pastas no apache:__

```nano /etc/apache2/ports.conf```

Troque a porta 80 ou qualquer outra que tiver pra qualquer outra porta,exemplo:

Listen 80 » Listen 8110

Salve o arquivo (Ctrl + O e Ctrl + X)

```service apache2 restart```

__Criar a pasta:__

```cd /var/www/html && mkdir server```

__Parte 4: Rodando Script pra testar__

```cd /root && ./onlineapp.sh```

Agora entre na IP+PORTA do seu server no diretório /server/online e veja se retornou algum número,exemplo:

http://149.56.184.155:8110/server/online

__Parte 5: Atualizando pelo cron__

Vamos trabalhar com a atualização dos users online no server a cada 1 min

```crontab -e```

Add no final do arquivo:

```*/1 * * * * cd  /root/ && ./onlineapp.sh```

Salve e feche o arquivo 

```service cron reload```

select-editor
EDITOR=nano crontab -e
