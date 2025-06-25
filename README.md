# ☕ AuthLite — API REST com Login + JWT

AuthLite é uma API RESTful em Java para autenticação segura com JWT. Possui arquitetura modular e escalável, integrando o protocolo MCP para comunicação padronizada com modelos de IA e o ADK para organizar agentes de software internos.

---

## 🚀 Visão Geral

AuthLite oferece um sistema completo para autenticação usando `access tokens` e `refresh tokens`, aliado a um controle flexível e seguro via **RBAC (Role-Based Access Control)**.

Além disso, o projeto está preparado para integração com modelos de inteligência artificial por meio do protocolo aberto **MCP**, que padroniza a troca de contexto entre o sistema e LLMs (Large Language Models).

Internamente, o sistema utiliza o **ADK**, que organiza a lógica em agentes independentes, responsáveis por funcionalidades específicas, facilitando manutenção, escalabilidade e testes.

---

## 💡 Funcionalidades Principais

- **Autenticação JWT** com emissão, validação e renovação de tokens (`access` e `refresh`).
- **Controle de acesso granular** baseado em roles e permissões (RBAC).
- **Filtros de segurança** para validação automática de tokens em requisições.
- Configuração flexível de **CORS** para múltiplas origens.
- Uso de **DTOs** para entrada e saída de dados, com tratamento padronizado de erros.
- Integração preparada com IA via protocolo **MCP** para fornecimento padronizado de contexto a LLMs.
- Arquitetura modular via **ADK**, com agentes especializados para autenticação, validação, renovação e gerenciamento.
- **Testes unitários e de integração** para garantir qualidade e confiabilidade.

---

## 🛠 Tecnologias

- **Java 17+**
- **Spring Boot**
- **Spring Security + JWT**
- **PostgreSQL / MySQL / H2** (desenvolvimento)
- **Maven**
- **MapStruct** (mapeamento DTOs)
- **Lombok**
- **JUnit 5 e Mockito** (testes automatizados)

---

## 🏗 Arquitetura

### MCP (Model-Context-Protocol)
**MCP** é um protocolo aberto que padroniza a forma como aplicações fornecem contexto para modelos de linguagem (LLMs) e sistemas de IA. No AuthLite, o MCP permite que o sistema envie dados e contexto estruturados para modelos inteligentes, viabilizando integrações futuras com recursos como análise comportamental, suporte automatizado ou auditoria inteligente.

### ADK (Agent Development Kit)
**ADK** é um kit para desenvolvimento de agentes de software autônomos, que executam tarefas específicas dentro do sistema. No AuthLite, agentes são responsáveis por funcionalidades como:

- Autenticação e emissão de tokens
- Validação de tokens em requisições
- Renovação via `refresh tokens`
- Gerenciamento de usuários e permissões

Cada agente atua como um módulo independente, comunicando-se por protocolos internos para garantir modularidade, isolamento de responsabilidades e facilidade de manutenção.

---

## 🔗 Endpoints Principais e Relação com MCP e ADK

| Método | Rota | Acesso | O que acontece (exemplo prático) | Como MCP e ADK atuam |
|---|---|---|---|---|
| **POST** | `/auth/login` | Público | Usuário envia credenciais, recebe `access` e `refresh tokens`. | **ADK:** Agente de autenticação valida dados e emite tokens. <br> **MCP:** Protocolo define fluxo da troca de contexto entre app e autenticação. |
| **POST** | `/auth/refresh` | Público | Usuário envia `refresh token`, recebe novo `access token`. | **ADK:** Agente de renovação verifica `refresh token` e emite novo `access token`. <br> **MCP:** Contexto atualizado e protocolo controla comunicação segura. |
| **POST** | `/auth/logout` | Usuário | Invalida tokens ativos para logout seguro. | **ADK:** Agente gerencia invalidação e limpeza de tokens. <br> **MCP:** Protocolo garante atualização do estado (contexto) de sessão. |
| **POST** | `/users/register` | Público | Cadastro de novo usuário. | **ADK:** Agente de gerenciamento cria usuário e associa permissões. <br> **MCP:** Modelo e contexto configuram dados e estado inicial do novo usuário. |
| **GET** | `/users/profile` | Usuário | Consulta dados do perfil logado. | **ADK:** Agente de validação assegura token válido. <br> **MCP:** Contexto da sessão autentica acesso ao modelo do perfil. |
| **PUT** | `/users/profile` | Usuário | Atualiza informações pessoais. | **ADK:** Agente atualiza dados no modelo do usuário. <br> **MCP:** Protocolo gerencia troca segura de dados e estado. |
| **GET** | `/admin/users` | Admin | Listagem de todos os usuários. | **ADK:** Agente verifica permissões de admin e consulta modelo. <br> **MCP:** Contexto e protocolo validam autorização e acesso. |
| **DELETE** | `/admin/users/{id}` | Admin | Remove usuário específico. | **ADK:** Agente remove usuário e atualiza banco. <br> **MCP:** Atualiza contexto do sistema refletindo a remoção. |

---

## 🔐 Controle de Acesso — RBAC

- Perfis como `ROLE_USER`, `ROLE_ADMIN`.
- Permissões associadas para proteger recursos.
- Validação automática no backend para garantir segurança.

---

## 🧪 Testes Automatizados

- Testes unitários para serviços, agentes e utilitários.
- Testes de integração para fluxos completos de autenticação e autorização.
- Execução via Maven ou Gradle (`mvn test` / `gradle test`).
- Cobertura focada na robustez e confiabilidade do sistema.

---

## 📥 Como Rodar

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/joaoclaudioprestes/AuthLite.git](https://github.com/joaoclaudioprestes/AuthLite.git)
    cd AuthLite
    ```

2.  **Configure o banco de dados** (`application.properties` ou variáveis de ambiente).

3.  **Ajuste as variáveis** para chaves JWT e conexões.

4.  **Execute a aplicação:**
    ```bash
    # Com Maven
    mvn spring-boot:run
    ```

5.  **Teste os endpoints** com Postman ou ferramentas similares.

---

## ✨ Contribuições

Contribuições são bem-vindas! Abra *issues* para reportar bugs ou sugerir melhorias e envie *pull requests*.

---

## 📄 Licença

Distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.