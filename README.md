# 👤 Usuario API

API REST de gestao de usuarios desenvolvida com Java 17 e Spring Boot 3, utilizando autenticacao JWT, PostgreSQL, Docker, CI/CD com GitHub Actions e integracao com a API ViaCEP.

---

## 🚀 Deploy Online

🔗 **Swagger**

Disponivel apos execucao local: `http://localhost:8080/swagger-ui/index.html`

---

## 🛠️ Tecnologias Utilizadas

- Java 17
- Spring Boot 3.2.5
- Spring Security
- JWT Authentication (jjwt 0.12.6)
- PostgreSQL
- Spring Data JPA
- Spring Cloud OpenFeign
- Docker
- Docker Compose
- Swagger / OpenAPI (SpringDoc)
- Lombok
- Gradle
- GitHub Actions (CI)

---

## 📋 Funcionalidades

### 👤 Usuarios

- Cadastro de usuarios com nome, email, senha, enderecos e telefones
- Login com JWT (Bearer Token)
- Busca de usuario por email
- Atualizacao de dados do usuario
- Exclusao de usuario por email

### 📍 Enderecos

- Cadastro de novos enderecos vinculados ao usuario
- Atualizacao de endereco por ID
- Consulta de endereco por CEP via API ViaCEP

### 📞 Telefones

- Cadastro de novos telefones vinculados ao usuario
- Atualizacao de telefone por ID

---

## 🔐 Seguranca

A aplicacao utiliza:

- Spring Security com filtro JWT
- Sessao stateless
- Senhas criptografadas com BCrypt
- Endpoints publicos: cadastro, login e consulta CEP
- Demais endpoints protegidos por token

---

## 🌐 Integracao ViaCEP

Utiliza **Spring Cloud OpenFeign** para consultar a API [ViaCEP](https://viacep.com.br/) e retornar dados completos de endereco a partir do CEP.

```
GET /usuario/endereco/{cep}
```

---

## 🔑 Endpoints

| Metodo | Rota | Auth | Descricao |
|--------|------|------|-----------|
| `POST` | `/usuario` | Nao | Cadastrar novo usuario |
| `POST` | `/usuario/login` | Nao | Login e obtencao do token JWT |
| `GET` | `/usuario?email=` | Sim | Buscar usuario por email |
| `DELETE` | `/usuario/{email}` | Sim | Deletar usuario por email |
| `PUT` | `/usuario` | Sim | Atualizar dados do usuario |
| `PUT` | `/usuario/endereco?id=` | Sim | Atualizar endereco por ID |
| `PUT` | `/usuario/telefone?id=` | Sim | Atualizar telefone por ID |
| `POST` | `/usuario/endereco` | Sim | Cadastrar novo endereco |
| `POST` | `/usuario/telefone` | Sim | Cadastrar novo telefone |
| `GET` | `/usuario/endereco/{cep}` | Nao | Consultar endereco por CEP |

---

## 🐳 Docker

A aplicacao possui configuracao completa com:

- **Dockerfile** multi-stage (build com Gradle + runtime com Eclipse Temurin 17)
- **Docker Compose** com PostgreSQL containerizado

### Executar localmente:

```bash
docker compose up --build
```

---

## 📂 Estrutura do Projeto

```
src/main
┣ controller        → Endpoints REST e tratamento de excecoes
┣ business           → Logica de negocio e servicos
┣ business/converter → Conversores DTO ↔ Entity
┣ business/dto       → Objetos de transferencia de dados
┣ infrastructure
┃ ┣ entity           → Entidades JPA (Usuario, Endereco, Telefone)
┃ ┣ repository       → Repositorios Spring Data JPA
┃ ┣ security         → Configuracao JWT e Spring Security
┃ ┣ clients          → Cliente Feign para ViaCEP
┃ ┗ exceptions       → Excecoes customizadas
```

---

## 📦 Como Executar Localmente

1. Clonar o projeto
```bash
git clone https://github.com/aureoandradedev/usuario.git
```

2. Entrar na pasta
```bash
cd usuario
```

3. Rodar com Docker
```bash
docker compose up --build
```

4. Acessar Swagger
```
http://localhost:8080/swagger-ui/index.html
```

---

## 👨‍💻 Autor

**Aureo Andrade**

- GitHub: [aureoandradedev](https://github.com/aureoandradedev)
- LinkedIn: [aureoandrade](https://www.linkedin.com/in/aureoandrade/)
