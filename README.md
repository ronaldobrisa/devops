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
A partir do Vagrant com provider Virtualbox serão provisionadas 3 Vms (Debian/AlmaLinux/Windows) que servirão de base para rodar todos os microserviços. Também a máquina AlamLinux provisionará o Ansible para realizar a gestão do ambiente. 

![Arquitetura](imagens/arquitetura.png)

## Pré-requisitos
Lista as ferramentas necessárias para rodar o projeto localmente.

Antes de rodar este projeto, você precisará de:
- [VirtualBox](https://www.virtualbox.org/wiki/Documentation) - criar e executar máquinas virtuais (VMs) em um único sistema físico.
- [Vagrant](https://www.vagrantup.com/docs) - gerenciamento e automação de máquinas virtuais.
- [Ansible](https://docs.ansible.com/ansible/latest/index.html) - automação de TI usada para gerenciar e configurar sistemas.

### Componentes principais

- **Docker**: Contêinerização da aplicação.
- **Kubernetes**: Orquestração de contêineres.
- **Terraform**: Infraestrutura como código.

## Como Rodar o Projeto
Passo a passo para clonar o repositório e configurar o ambiente.

### 1. Clonar o repositório
```bash
git clone https://github.com/usuario/nome-do-projeto.git
cd nome-do-projeto
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