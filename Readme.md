# Projeto de Automação com Vagrant e Ansible

## Integrantes da Equipe

- Nome 1 = Jose Jantony da Silva Floriano
- Nome 2 = Jonatas Gabriel Evangelista da Silva

**Disciplina:** Administração de Sistemas Abertos  
**Professor:** Leonidas Francisco de Lima Júnior
---

## Descrição do Projeto

Este projeto tem como objetivo provisionar e configurar automaticamente um ambiente composto por múltiplas máquinas virtuais utilizando Vagrant e Ansible. O ambiente simula uma infraestrutura composta por servidores de arquivos, banco de dados, aplicação e cliente.

### Estrutura das Máquinas Virtuais

- **arq**: Servidor de arquivos, com hostname `arq.jantony.jonatas.devops`, IP fixo `192.168.56.124` e três discos adicionais de 10GB cada.
- **db**: Servidor de banco de dados, hostname `db.jantony.jonatas.devops`, IP via DHCP.
- **app**: Servidor de aplicação, hostname `app.jantony.jonatas.devops`, IP via DHCP.
- **cli**: Máquina cliente, hostname `cli.jantony.jonatas.devops`, IP via DHCP, 1024MB de RAM.

Todas as máquinas utilizam a box `debian/bookworm64` e o provedor VirtualBox.

---

## Como Executar o Projeto

### Pré-requisitos

- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)
- [Ansible](https://www.ansible.com/) 

### Passos para Execução

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/jantonytony2023/asa_projeto.git
   cd asa_projeto
   ```

2. **Suba as máquinas virtuais:**
   ```bash
   vagrant up
   ```

3. **Execute os playbooks do Ansible:**
   - Os playbooks estão localizados na pasta `ansible/`.
   - Exemplo de execução:
     ```bash
     cd /vagrant/ansible
     ansible-playbook -i hosts arq_playbook.yml
     ```

---

## Organização do Projeto

```
.
├── ansible
│   ├── app_playbook.yml
│   ├── arq_playbook.yml
│   ├── cli_playbook.yml
│   ├── common_config.yml
│   ├── db_playbook.yml
│   ├── files
│   │   ├── jantony.pub
│   │   ├── jonatas.pub
│   │   └── ssh_banner.txt
│   └── hosts
└── Vagrantfile

```

- **Vagrantfile**: Define as máquinas virtuais e suas configurações.
- **ansible/**: Contém os playbooks e arquivos de configuração do Ansible.
- **README.md**: Documentação do projeto.

---

## Observações

- Certifique-se de que seu usuário tenha permissão para executar o VirtualBox.
- Os playbooks do Ansible podem ser adaptados conforme a necessidade do projeto.

---

## Contato

Dúvidas ou sugestões, entre em contato com a equipe ou o professor responsável.
