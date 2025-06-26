# ☕ AuthLite — API REST com Login + JWT

AuthLite é uma API RESTful em Java para autenticação segura com JWT. Possui arquitetura modular e escalável, ideal para sistemas que exigem controle de acesso robusto e confiável.

---

## 🚀 Visão Geral

AuthLite oferece um sistema completo para autenticação usando `access tokens` e `refresh tokens`, aliado a um controle seguro via **RBAC (Role-Based Access Control)**.

A aplicação valida tokens automaticamente nas requisições, permite atualização de sessões e gerenciamento de perfis de forma segura.

---

## 💡 Funcionalidades Principais

- **Autenticação JWT** com emissão, validação e renovação de tokens (`access` e `refresh`).
- **Controle de acesso granular** baseado em roles e permissões (RBAC).
- **Filtros de segurança** para validação automática de tokens.
- Configuração flexível de **CORS** para múltiplas origens.
- Uso de **DTOs** para entrada e saída de dados.
- Tratamento padronizado de erros.
- **Testes unitários e de integração** para garantir qualidade e confiabilidade.

---

## 🛠 Tecnologias

- **Java 17+**
- **Spring Boot**
- **Spring Security + JWT**
- **PostgreSQL / MySQL / H2** (ambiente de desenvolvimento)
- **Maven**
- **MapStruct** (mapeamento DTOs)
- **Lombok**
- **JUnit 5 e Mockito** (testes automatizados)

---

## 🔗 Endpoints Principais

| Método | Rota | Acesso | Descrição |
|--------|------|--------|-----------|
| **POST** | `/auth/login` | Público | Usuário envia credenciais e recebe tokens JWT. |
| **POST** | `/auth/refresh` | Público | Envia `refresh token` e recebe novo `access token`. |
| **POST** | `/auth/logout` | Usuário | Invalida os tokens para logout seguro. |
| **POST** | `/users/register` | Público | Cadastro de um novo usuário. |
| **GET** | `/users/profile` | Usuário | Consulta os dados do perfil logado. |
| **PUT** | `/users/profile` | Usuário | Atualiza as informações pessoais. |
| **GET** | `/admin/users` | Admin | Lista todos os usuários do sistema. |
| **DELETE** | `/admin/users/{id}` | Admin | Remove um usuário específico. |

---

## 🔐 Controle de Acesso — RBAC

- Perfis como `ROLE_USER`, `ROLE_ADMIN`.
- Permissões associadas para proteger recursos.
- Validação automática no backend para garantir segurança de acesso.

---

## 🧪 Testes Automatizados

- **Testes unitários** para serviços e utilitários.
- **Testes de integração** cobrindo o fluxo completo de autenticação.
- Executáveis via Maven:
  ```bash
  mvn test

---

## 📥 Como Rodar

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/joaoclaudioprestes/AuthLite.git
   cd AuthLite
   ```

2. **Configure o banco de dados** em `application.properties` ou via variáveis de ambiente.

3. **Ajuste as variáveis sensíveis** (como chaves JWT).

4. **Execute a aplicação:**


   ```bash
   mvn spring-boot:run
   ```

5. **Teste os endpoints** com Postman, Insomnia ou qualquer cliente HTTP.

---

## ✨ Contribuições

Contribuições são bem-vindas! Abra uma *issue* para reportar bugs ou sugerir melhorias. Pull requests são avaliados com atenção.

---

## 📄 Licença

Distribuído sob a licença MIT. Consulte o arquivo `LICENSE` para mais informações.

