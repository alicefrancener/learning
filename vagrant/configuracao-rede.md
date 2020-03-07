# Configuração da rede

Conectados à máquina virtual (com `vagrant ssh`), para instalar um serviço como o servidor Nginx devemos atualizar a lista de pacotes e depois instalar o programa.

```bash
sudo apt-get update

sudo apt-get install -y nginx
```

O Nginx já estará rodando e para confirmar usar `netstat -lntp`. Há outro comando de envio de requisição - `curl http://localhost` - que  devolve em html uma confirmação de que o web server está rodando.

## Forward Ports

<small>Vagrant > Networking > [Forward Ports](https://www.vagrantup.com/docs/networking/forwarded_ports.html)</small>

Podemos usar uma porta específica em Windows, o qual recebe a requisição e acessa a máquina virtual automaticamente através do processo de *Port Forwarding* na rede. Para definir esta chamada, é necessário adicionar a linha de configuração network no arquivo "Vagrantfile", alterando para o host do Windows e salvando:

```ruby
Vagrant.configure("2") do |config|
    config.vm.network "forwarded_port", guest: 80, host:8080
end
```
 
O `host` é o hospedeiro (o sistema que permite o guest (convidado) rodar) e o `guest` é a máquina virtual.

Depois é necessário parar a máquina virtual (`vagrant halt`) e subir de novo (`vagrant up`) para que essa configuração seja aplicada.
E depois, acessando o navegador com `localhost:8080` irá aparecer a página html que foi retornada com o comando `curl http://localhost` na máquina virtual!

## Rede privada (*static* ou *dhcp*)

As configurações de rede privada permitem acessar a máquina virtual somente através do host - seu computador.

<small>Vagrant > Networking > [Private Network](https://www.vagrantup.com/docs/networking/private_network.html)</small>

> Vagrant private networks allow you to access your guest machine by some address that is not publicly accessible from the global internet. In general, this means your machine gets an address in the private address space.

### DHCP

> The easiest way to use a private network is to allow the IP to be assigned via DHCP.

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "private_network", type: "dhcp"
end
```

Para aplicar essa configuração, talvez seja necessário destruir a máquina e recriá-la (não esquecer de instalar novamente nginx).

São apresentados dois adaptadores: `nat` e `hostonly`. Ao executar `ipconfig` podemos ver as entradas no Windows. Posso usar o IP no navegador. 

### IP estático

> You can also specify a static IP address for the machine. This lets you access the Vagrant managed machine using a static, known IP. The Vagrantfile for a static IP looks like this:

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.50.4"
end
```
## Rede pública (*static* ou *dhcp*)

As configuração de rede pública permitem acessar a máquina virtual através dos computadores em uma única rede pública.

<small>Vagrant > Networking > [Private Network](https://www.vagrantup.com/docs/networking/public_network.html)</small>

### DHCP

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "public_network"
end
```

São apresentados dois adaptadores: `nat` e `bridged`.

### IP estático

```ruby
Vagrant.configure("2") do |config|
    config.vm.network "public_network", ip: "192.168.1.24"
end
```