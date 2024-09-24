# Tipos de Bancos de Dados em uma Aplicação

Em uma aplicação, geralmente você teria **dois tipos principais** de bancos de dados, além de um **opcional**, dependendo do fluxo de desenvolvimento:

## :hammer_and_wrench: Banco de Dados de Desenvolvimento

Esse banco é utilizado pelos desenvolvedores durante o desenvolvimento da aplicação. Ele permite testar mudanças de código em um ambiente controlado.

- **Características**: 
  - Pode ser uma cópia simplificada do banco de produção ou um banco de dados menos robusto, já que a prioridade aqui é a velocidade de desenvolvimento.
- **Exemplo**: 
  - SQLite, MySQL local.
  
- **Nome**: 
  Se a aplicação se chama `Sistema Gestão de Clientes`, o nome do banco de dados poderia ser:
  - `gestao_clientes_desenvolvimento`
  - `desenvolvimento_gestao_clientes`

---

## :white_check_mark: Banco de Dados de Homologação (Staging)

Esse banco é usado para testar a aplicação antes de ser colocada em produção. Ele deve ser uma réplica do banco de produção para garantir que o ambiente de teste seja o mais próximo possível do ambiente real.

- **Características**: 
  - Utilizado por testadores e em processos de QA para validar novas funcionalidades e encontrar bugs antes do lançamento oficial.
- **Exemplo**: 
  - Uma réplica do banco de produção.
  
- **Nome**: 
  Se a aplicação se chama `Sistema Gestão de Clientes`, o nome do banco de dados poderia ser:
  - `gestao_clientes_homologacao`
  - `homologacao_gestao_clientes`

---

## :lock: Banco de Dados de Produção

Esse banco armazena os dados reais de usuários e operações em tempo real. Ele é a versão final e "ao vivo" da aplicação, que está sendo usada pelos clientes ou pelo público.

- **Características**: 
  - Deve ser altamente disponível, seguro e escalável, com backups e monitoramento contínuo.
- **Exemplo**: 
  - PostgreSQL, MySQL, MongoDB.
  
- **Nome**: 
  Se a aplicação se chama `Sistema Gestão de Clientes`, o nome do banco de dados poderia ser:
  - `gestao_clientes_producao`
  - `producao_gestao_clientes`

---

## :test_tube: Outros Bancos Opcionais

### Banco de Dados de Testes Unitários

Usado para testes automatizados e unitários, onde você verifica funcionalidades específicas de forma isolada. Pode ser um banco em memória ou uma versão mais leve.

- **Nome**: 
  Se a aplicação se chama `Sistema Gestão de Clientes`, o nome do banco de dados poderia ser:
  - `gestao_clientes_testes`
  - `testes_gestao_clientes`

---

### Exemplos de uso de bancos:

| Tipo                    | Exemplo de Nome                     |
|-------------------------|--------------------------------------|
| Desenvolvimento          | `gestao_clientes_desenvolvimento`   |
| Homologação              | `gestao_clientes_homologacao`       |
| Produção                 | `gestao_clientes_producao`          |
| Testes Unitários         | `gestao_clientes_testes`            |

---

