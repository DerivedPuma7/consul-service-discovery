# consul-service-discovery
## Intruções:
- suba os containeres docker:
    - > docker compose up -d
- #cada container representa uma máquina, um server
- acesse o container consulserver01 e inicialize o consul server
    - descubra o ip com:
        - > ifconfig
    - crie os diretórios de dados e config do consul
        - > mkdir /var/lib/consul
        - > mkdir /etc/consul.d
    - execute o comando para criar o consul server
        - -bootstrap-expect representa o numero de máquinas que deseja criar
        - -node representa qual o nó, qual o server
        - -bind representa o ip
        - -data-dir e -config-dir são os diretorios que criamos anteriormente
        - > consul agent -server -bootstrap-expect=3 -node=consulserver01 -bind=172.21.0.2 -data-dir=/var/lib/consul -config-dir=/etc/consul.d
    - pronto, já tem um server consul rodando
- repita o processo para os outros 2 containeres e ao fim, faça com que cada server reconheça o outro, com:
    - > consul join ipQueDesejaUnir
- verifique se está tudo certo com:
    - > consul members
        - estará certo se o cluster com as 3 máquinas aparecerem 