# DevOps Project - [Nome do Projeto]

## Índice

1. [Visão Geral](#visão-geral)
2. [Arquitetura](#arquitetura)
3. [Pré-requisitos](#pré-requisitos)
4. [Como Rodar o Projeto](#como-rodar-o-projeto)
5. [Automação e Pipelines](#automação-e-pipelines)
6. [Monitoramento e Logs](#monitoramento-e-logs)
7. [Testes e Validações](#testes-e-validações)
8. [Contribuindo](#contribuindo)
9. [Licença](#licença)

## Visão Geral 
O objetivo do projeto é pavimentar um caminho sólido para a formação como profissional devops.
Os recursos utilizados serão principalmente Vagrant para provisionamento de máquinas virtuais e Ansible para gestão do provisionamento.

## Arquitetura 
A partir do Vagrant como provider Virtualbox serão provisionadas 3 Vms (Debian/AlmaLinux/Windows) que servirão de base para rodar todos os microserviços. Também a máquina AlamLinux provisionará o Ansible para realizar a gestão do ambiente. 

![Arquitetura](imagens/arquitetura.png)

## Pré-requisitos
Lista as ferramentas necessárias para rodar o projeto localmente.

Antes de rodar este projeto, você precisará de:
- [VirtualBox](https://www.virtualbox.org/wiki/Documentation) - criar e executar máquinas virtuais (VMs) em um único sistema físico.
- [Vagrant](https://www.vagrantup.com/docs) - gerenciamento e automação de máquinas virtuais.
- [Ansible](https://docs.ansible.com/ansible/latest/index.html) - automação de TI usada para gerenciar e configurar sistemas.

### Componentes principais

- **Virtualbox**: Virtualizar ambientes para testar, desenvolver e rodar sistemas operacionais diferentes sem a necessidade de hardware físico.
- **Vagrant**: cria e gerencia ambientes de desenvolvimento e de teste de maneira simples e eficiente, usando uma configuração baseada em Vagrantfile.
- **Ansible**: utilizado para orquestrar e provisionar servidores de maneira automatizada, garantindo que ambientes estejam configurados da mesma maneira.

## Como Rodar o Projeto
Passo a passo para clonar o repositório e configurar o ambiente.

### 1. Clonar o repositório (Vscode)
```bash
git clone https://github.com/ronaldobrisa/devops.git
cd devops
```
### 2.Instalar o VirtualBox 
Para este projeto será usado a versão para WindowsSO que consiste em realizar o download e seguir os passos de instalação do executável.

### 3.Instalar o Vagrant
Para este projeto será usado a versão para WindowsSO que consiste em realizar o download e seguir os passos de instalação do executável.

### 4.Iniciar o Vagrant no Vscode


```bash
# Iniciar o Vagrant
vagrant init
```

### 5.Configurar o Vagrantfile e provisionar Vms

```bash

Vagrant.configure("2") do |config|
config.vm.provider "virtualbox" do |vb|
vb.gui = false
end

# Debian Server

config.vm.define "debian" do |debian|
debian.vm.box = "debian/bullseye64"
debian.vm.hostname = "Debian-VM"
debian.vm.network "private_network", type: "dhcp"
debian.vm.provider "virtualbox" do |vb|
vb.name = "Debian-VM-Lab"
vb.memory = "1024"
vb.cpus = 2
end
end

# AlmaLinux Server

config.vm.define "almalinux" do |almalinux|
almalinux.vm.box = "almalinux/8"
almalinux.vm.hostname = "AlmaLinux-VM"
almalinux.vm.network "private_network", type: "dhcp"
almalinux.vm.provider "virtualbox" do |vb|
vb.name = "AlmaLinux-VM-Lab"
vb.memory = "1024"
vb.cpus = 2
end
end

# Windows Server

config.vm.define "windows" do |windows|
windows.vm.box = "mcree/win2019"
windows.vm.hostname = "Windows-VM"
windows.vm.network "private_network", type: "dhcp"
windows.vm.provider "virtualbox" do |vb|
vb.name = "Windows-VM-Lab"
vb.memory = "2048"
vb.cpus = 2
end
end
end
```

### 6.Instalar o Ansible na Vm AlmaLinux

```bash
#Enable EPEL repository:
sudo dnf install epel-release -y

#Install Ansible:
sudo dnf install ansible -y

#Verify Installation:
ansible --version
```

### 7.Criar e configurar um playbook
Um playbook Ansible é um arquivo YAML que define o que deve ser feito em seus servidores (instalar pacotes, configurar serviços, etc.). Ele é usado para automatizar e orquestrar configurações em múltiplos hosts.

1. Acesse a máquina virtual onde você instalou o Ansible (no caso, a máquina virtual AlmaLinux).

Estrutura de Diretórios Sugerida:

Aqui está uma estrutura comum para organizar seus arquivos de playbook e configuração do Ansible:

```bash
/ansible_project
    ├── inventory/                # Arquivos de inventário (hosts)
    ├── playbooks/                # Diretório onde os playbooks serão armazenados
        ├── install_apache.yml
        ├── setup_nginx.yml
    ├── roles/                    # Funções (roles) do Ansible (se necessário)
    ├── group_vars/               # Variáveis para grupos de hosts
    ├── host_vars/                # Variáveis para hosts individuais
    └── ansible.cfg               # Arquivo de configuração do Ansible
```

2. Crie um diretório para o projeto Ansible (se ainda não tiver um):

```bash
mkdir -p /home/vagrant/ansible_project/playbooks
```

3. Coloque o seu playbook dentro do diretório playbooks/. Por exemplo:

```bash
nano /home/vagrant/ansible_project/playbooks/playbook_devops.yml
```

### 8. Configuração do Inventário
Em um arquivo de inventário, você pode definir os hosts ou grupos de hosts.

```bash
all:
  hosts:
    almalinux:
      ansible_host: #ip
  children:
    webservers:
      hosts:
        almalinux:
    databases:
      hosts:
        db_server:
```


## Automação e Pipelines
Descreve a configuração e os passos do pipeline CI/CD.

A automação do fluxo de trabalho é realizada através de pipelines no Jenkins. O pipeline CI/CD é responsável por:
Build: Compilar e testar o código da aplicação.
Testes: Executar testes unitários e de integração.
Deploy: Realizar o deploy da aplicação nos ambientes de desenvolvimento, homologação e produção.
Monitoramento: Integrar com Prometheus e Grafana para monitoramento de performance e disponibilidade.

## Monitoramento e Logs
Como a solução lida com o monitoramento e gerenciamento de logs.

O monitoramento da aplicação é feito utilizando Prometheus e Grafana para métricas, e ELK Stack para gerenciamento de logs. Certifique-se de que esses componentes estão corretamente configurados em sua infraestrutura.
Para acessar o painel do Grafana:
Acesse a URL: http://<IP-do-servidor>:3000
Login: admin / admin

## Testes e Validações
Como executar os testes automatizados do projeto.

O projeto inclui testes automatizados de unidade, integração e performance. Para executar os testes localmente, você pode usar os seguintes comandos:

### Testes unitários
./gradlew test

### Testes de integração
./gradlew integrationTest

## Contribuindo
Instruções para quem quiser contribuir com o projeto.

Contribuindo
Se você deseja contribuir para este projeto, siga os seguintes passos:

## Licença
Tipo de licença do projeto, garantindo que as pessoas saibam como usá-lo legalmente.

Licença
Este projeto está licenciado sob a Licença MIT.