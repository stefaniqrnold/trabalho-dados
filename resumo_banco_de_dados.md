
# Resumo de Banco de Dados – Engenharia de Software (UNIJUI)

## 1. Três Limitações do Enfoque Tradicional de Armazenamento de Dados

### a) Redundância e inconsistência de dados
Quando os mesmos dados são armazenados em vários arquivos diferentes, pode ocorrer repetição desnecessária e conflitos entre os dados.

**Exemplo:** O nome de um cliente aparece em dois arquivos diferentes com grafias distintas.

### b) Difícil acesso a dados
Sistemas de arquivos exigem programação para cada tipo de consulta. Não há uma linguagem padrão como SQL.

**Exemplo:** Buscar pedidos de um cliente exige lógica programada.

### c) Falta de segurança e controle de acesso
Não há controle refinado de acesso a dados sensíveis.

**Exemplo:** Qualquer pessoa pode editar um arquivo de salários.

---

## 2. Por que escolher um SGBD ao invés de um sistema de arquivos tradicional?

- Redução de redundância e inconsistência
- Facilidade no acesso e manipulação dos dados via SQL
- Segurança e controle de acesso
- Multiusuário e concorrência segura
- Facilidade de backup e recuperação

---

## 3. Linguagens dos SGBDs

### a) DDL (Data Definition Language)
Define estrutura do banco de dados (tabelas, campos, etc).  
**Exemplo:** `CREATE TABLE Aluno (ID INT, Nome VARCHAR(100));`

### b) DML (Data Manipulation Language)
Manipula os dados: inserção, consulta, atualização e remoção.  
**Exemplo:** `SELECT * FROM Aluno;`

---

## 4. Vantagens de um SGBD

- Redução de redundância
- Garantia de integridade dos dados
- Controle de segurança e acesso

---

## 5. Tipos de Usuários de um Banco de Dados

- **DBA:** Administra o banco, segurança, backups etc.
- **Desenvolvedores:** Criam aplicações que interagem com o BD
- **Usuários finais:** Usam o sistema sem acessar diretamente o BD
- **Analistas de dados:** Extraem insights via consultas

---

## 6. Exemplo de uso de arquivos em vez de banco de dados

Sistema simples de lista de tarefas para um único usuário, com arquivos `.txt` ou `.json`, sem necessidade de controle de acesso ou grandes volumes de dados.

---

## 7. Responsabilidades de um DBA

- Modelar e manter o banco de dados
- Definir segurança e permissões
- Monitorar desempenho
- Realizar backups e recuperação
- Gerenciar usuários e estrutura do BD

---

## 8. Redundância controlada de dados

Repetição planejada, com controle do SGBD para manter integridade.  
**Exemplo:** Nome do cliente armazenado em pedidos, atualizado em cascata.

---

## 9. Problemas dos sistemas de arquivos resolvidos por bancos de dados

### a) Acesso complexo aos dados
Resolvido com SQL

### b) Inconsistência de dados
Resolvido com controle de integridade e normalização

---

## 10. Independência Lógica vs. Física

- **Lógica:** Alterações na estrutura sem afetar os programas
- **Física:** Alterações na forma de armazenamento sem afetar a lógica

---

## 11. Redundância controlada vs. não controlada

- **Controlada:** Intencional e com regras de integridade.  
  Ex: Nome do cliente em pedidos, com atualizações automáticas.

- **Não controlada:** Sem planejamento, sujeita a erros e inconsistências.  
  Ex: Nome duplicado com variações em vários arquivos.

---

## 12. Sistema Acadêmico – Entidades e Relacionamentos

### Entidades:

**Aluno:** matrícula, nome, email  
**Disciplina:** código, nome, carga horária  
**Professor:** matrícula, nome, departamento

### Relacionamentos:

- **Aluno — cursa — Disciplina:** (N:N)  
- **Professor — leciona — Disciplina:** (1:N)

---

## 13. Questões com base no diagrama (ER da aula)

### 1. Descrição do diagrama:
Cada aluno se matricula em várias disciplinas. Cada disciplina pode ser cursada por vários alunos. A nota é armazenada no relacionamento entre aluno e disciplina.

### 2. Quatro elementos:
- Entidade
- Atributo
- Relacionamento
- Atributo identificador (chave)

### 3. Redundância de dados e suas diferenças
(Resposta igual à questão 11)

### 4. Redundância na tabela EMPREGADO?
Sim, nome do gerente pode estar repetido. Pode-se normalizar em uma nova tabela "Departamento".

### 5. Quando a redundância é desejada?
- Para otimizar desempenho
- Em sistemas distribuídos
- Em históricos

### 6. Desvantagem da redundância?
- Inconsistência dos dados
- Desperdício de espaço
- Dificuldade de manutenção

---
