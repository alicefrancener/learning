# Lidando com o SSH

## Autenticação com chave privada gerada automaticamente pelo vagrant

O Vagrant gera automaticamente um par de chaves SSH. A chave pública fica na máquina virtual (guest), a chave privada fica no host. 
O comando `vagrant ssh-config` lista as configurações SSH que o comando `vagrant ssh` usará.

```bash
# tentando se conectar com ssh (essa tentativa gera um erro)
ssh vagrant@192.168.50.4
```

- No arquivo .ssh/known_host fica guardado o *fingerprint* de cada máquina com a qual o SSH se conectou. 
- Como criamos máquinas através do Vagrant com frequência, a ID muda e é preciso limpar esse arquivo ou apagá-lo quando der esse erro.

```bash
# apagar
rm .ssh/known_hosts

# tentando se conectar novamente utilizando a chave privada gerada automaticamente
ssh -i .vagrant/machines/default/virtualbox/private_key vagrant@192.168.50.4
```

## Autenticação com chave privada gerada manualmente

```bash
# gerar uma chave
## o sistema pede para escolher local para salvar
## caso queira, pode criar senha para proteger a chave
ssh-keygen -t rsa

# copiar a chave publica para a máquina virtual
## a - acessar a máquina
vagrant ssh
## b - acessar a pasta automaticamente montada pelo Windows
ls /vagrant/
## c - copiar a chave da pasta vagrant para a máquina
cp /vagrant/id_bionic.pub
## d - adicionar ao arquivo authorized_keys
cat id_bionic.pub >> .ssh/authorized_keys
```

Agora, saindo da máquina virtual e retornando ao host usamos a chave privada para nos conectar remotamente à máquina virtual baseado em uma chave pública/privada.

```bash
ssh -i id_bionic vagrant@192.168.50.4
```