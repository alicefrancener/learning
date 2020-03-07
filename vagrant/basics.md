# Primeiros passos

## Instalar

- Instalar **Vagrant**
- Instalar Hypervisor (monitor de máquina virtual): no caso utilizei [VirtualBox](https://www.vagrantup.com/docs/virtualbox/) compatível com Vagrant

## Criar e subir máquina virtual

- Criar um diretório para os arquivos
- Escolher [box](https://www.vagrantup.com/intro/getting-started/boxes.html)

```bash
# criar diretorio
mkdir <nome-do-diretorio>
cd <nome-do-diretorio>

# definir configurações da máquina virtual (nesse caso Ubuntu 12.04 => hashicorp/precise64) - cria o arquivo Vagrantfile
vagrant init <box-name>
vagrant init hashicorp/precise64

# criar (baixar e importar a box) e aplicar as configurações da máquina virtual
vagrant up
```

## Checar status

```bash
vagrant status
```

Na VirtualBox também é possível ver o status e se está funcionando.

## Conectar à máquina virtual com `ssh`

```bash
vagrant ssh

# mostra as configurações ssh
vagrant ssh-config

# desconectar da máquina
logout
exit
```

## Comandos básicos

```bash
# subir a máquina
vagrant up

# para a máquina
vagrant halt

# destruir a máquina
vagrant destroy

# reload da máquina (vagrant halt && vagrant up)
vagrant reload
```

[Vagrant > Comandos](https://www.vagrantup.com/docs/cli/)