# Vagrant Docker Swarm Cluster

Este projeto cria um ambiente virtualizado com **4 máquinas virtuais** usando **Vagrant** e **VirtualBox**, configuradas para formar um cluster **Docker Swarm** com:

- 1 nó gerenciador (`master`)
- 3 nós trabalhadores (`node01`, `node02`, `node03`)

## 🔧 Requisitos

Antes de começar, certifique-se de ter os seguintes softwares instalados na sua máquina:

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)
- (Opcional) [VS Code](https://code.visualstudio.com/) com extensão **Ruby** para melhor leitura do `Vagrantfile`

## 📁 Estrutura do Projeto

```
📦 vagrant-swarm-cluster
├── Vagrantfile
└── README.md
```

## 🚀 Como usar

1. Clone este repositório ou baixe os arquivos:
   ```bash
   git clone https://github.com/seu-usuario/vagrant-swarm-cluster.git
   cd vagrant-swarm-cluster
   ```

2. Inicialize o ambiente:
   ```bash
   vagrant up
   ```

   Isso irá:
   - Criar 4 máquinas virtuais
   - Instalar o Docker em todas elas
   - Configurar o nó `master` como **manager**
   - Incluir os nós `node01`, `node02`, e `node03` como **workers** no cluster

3. Acesse uma VM (exemplo: master):
   ```bash
   vagrant ssh master
   ```

4. Verifique o status do cluster:
   ```bash
   docker node ls
   ```

## ⚙️ Especificações Técnicas

- **Box usada**: `ubuntu/bionic64`
- **Recursos por VM**:
  - CPU: 1
  - RAM: 2048 MB
  - Discos adicionais: 2 discos de 20GB cada (total de 3 discos por VM)
- **IP fixo das VMs**:
  - `master`: 192.168.56.10
  - `node01`: 192.168.56.11
  - `node02`: 192.168.56.12
  - `node03`: 192.168.56.13

## 🗑️ Como destruir o ambiente

Caso queira remover todas as VMs e limpar o ambiente:

```bash
vagrant destroy -f
```

## 📝 Observações

- Os discos adicionais são criados, mas **não são particionados nem montados automaticamente**. Caso queira utilizá-los dentro do sistema, será necessário configurar isso manualmente ou incluir um script adicional.
- O `worker_token` é salvo temporariamente em `/vagrant/worker_token` para facilitar a junção dos workers ao cluster.

---

Feito com ☕ e Vagrant, por Luiz Carlos França