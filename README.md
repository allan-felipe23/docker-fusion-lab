# 🐳 Fusion Project - Docker Orchestration

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)

Este repositório contém a implementação prática de uma arquitetura de microsserviços containerizados, orquestrando uma aplicação **Django** (Web) conectada a um banco de dados **PostgreSQL** utilizando **Docker Compose**.

O objetivo do projeto é demonstrar conhecimentos em infraestrutura ágil, redes isoladas e persistência de dados.

## 🏗 Arquitetura

O ambiente é composto por dois serviços principais definidos no `docker-compose.yml`:

* **App (Fusion):** Aplicação Python/Django rodando em container Alpine Linux.
* **Database (DB):** Banco de dados PostgreSQL 13 com persistência via Volumes.

**Funcionalidades de Infraestrutura:**
* **Isolamento de Rede:** Comunicação interna via DNS do Docker (Service Discovery).
* **Persistência:** Uso de Named Volumes (`pgdata`) para garantir que os dados sobrevivam ao ciclo de vida dos containers.
* **Hot-Reload:** Configuração de Bind Mounts para desenvolvimento, permitindo que alterações no código local reflitam instantaneamente no container.
* **Variáveis de Ambiente:** Injeção de credenciais de banco via environment variables.

## 🚀 Como Executar

### Pré-requisitos
* Docker e Docker Compose instalados.

### Passo a Passo

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/SEU_USUARIO/docker-fusion-lab.git](https://github.com/SEU_USUARIO/docker-fusion-lab.git)
    cd docker-fusion-lab
    ```

2.  **Suba a infraestrutura:**
    ```bash
    docker-compose up -d --build
    ```

3.  **Execute as migrações do banco:**
    Como o banco é iniciado vazio, precisamos criar as tabelas do Django:
    ```bash
    docker-compose exec web python manage.py migrate
    ```

4.  **Crie um superusuário (Opcional):**
    ```bash
    docker-compose exec web python manage.py createsuperuser
    ```

5.  **Acesse:**
    * Aplicação: [http://localhost:8000](http://localhost:8000)
    * Painel Admin: [http://localhost:8000/admin](http://localhost:8000/admin)

## 🛠 Comandos Úteis

* **Ver logs em tempo real:** `docker-compose logs -f`
* **Derrubar o ambiente:** `docker-compose down`
* **Reconstruir imagens:** `docker-compose up -d --build --force-recreate`

## 👨‍💻 Autor

**Allan Felipe Antunes Borges**
*Analista Cloud AWS em formação*
