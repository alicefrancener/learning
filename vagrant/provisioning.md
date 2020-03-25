# Provisioning

- Provisionamento significa instalar e configurar tudo o que for necessário para rodar algum serviço ou aplicação
- Para usar o Shell Provisionar, basta definir um script com os passos de instalação:

```bash
Vagrant.configure("2") do |config|
config.vm.provision "shell", path: "script.sh"
end
```

Os comandos do Shell Provisioner também podem ser usados de maneira inline ou remoto:

```bash
$script = <<-SCRIPT
  echo Instalando MySQL
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $script
end
```

- O Vagrant automaticamente compartilha uma pasta entre o host e o guest (Synced Folder)
- Por padrão, é compartilhada a pasta onde se encontra o Vagrantfile
- Na máquina guest, podemos acessar a pasta pelo caminho `/vagrant`
- A pasta compartilhada pode ser reconfigurada no Vagrantfile: `config.vm.synced_folder "src/", "/public"`

***

https://www.vagrantup.com/docs/provisioning/shell.html