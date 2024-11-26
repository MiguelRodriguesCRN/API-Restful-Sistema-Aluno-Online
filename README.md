# Projeto AlunoOnline

Este projeto é um sistema de gestão acadêmica abrangente, desenvolvido durante as aulas com o apoio do Professor Kelson Almeida. A aplicação foi construída utilizando o robusto framework Spring Boot, o que proporciona uma infraestrutura sólida e escalável para o sistema.

O sistema oferece uma ampla gama de funcionalidades para gerenciar todos os aspectos da vida acadêmica, incluindo alunos, professores, disciplinas e matrículas. A aplicação permite que os usuários realizem diversas operações de forma intuitiva e eficiente, como criar, listar, buscar, atualizar e excluir registros relacionados a esses elementos-chave.

Uma das principais funcionalidades do sistema é o gerenciamento de matrículas dos alunos. Os usuários podem realizar operações essenciais, como realizar a matrícula de um estudante em uma disciplina, solicitar o trancamento de uma matrícula e atualizar as notas dos alunos ao longo do semestre. Essa abordagem holística simplifica significativamente o gerenciamento do fluxo acadêmico, permitindo que coordenadores, professores e funcionários administrativos mantenham um controle preciso e organizado sobre todas as informações relevantes.

## Sumário

- [Arquitetura do Projeto](#arquitetura-do-projeto)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Operações Disponíveis](#operações-disponíveis)
- [Como Executar](#como-executar)
- [Licença](#licença)

## Arquitetura do Projeto

O sistema segue uma arquitetura padrão de **camadas** para facilitar a manutenção e escalabilidade:

1. **Controller**: A camada de controladores expõe os endpoints da API e gerencia as requisições HTTP.
2. **Service**: Contém a lógica de negócio do sistema.
3. **Repository**: Responsável pelas operações de persistência de dados no banco de dados.
4. **DTO (Data Transfer Object)**: Usados para transportar dados entre as camadas sem expor diretamente as entidades do banco.

### Fluxo de Operação

1. **Entrada (Request)**: O cliente envia uma requisição HTTP.
2. **Controller**: O controlador manipula a requisição e chama a camada de serviço.
3. **Service**: A camada de serviço executa a lógica de negócio.
4. **Repository**: O serviço acessa o repositório para persistir ou recuperar dados.
5. **Resposta (Response)**: O controlador envia a resposta ao cliente, contendo os dados ou status da operação.

## Estrutura do Projeto

### 📁 **config**
Contém configurações do sistema, incluindo a configuração do Swagger para gerar a documentação da API.

- **SwaggerConfig**: Configuração do Swagger para gerar a documentação interativa da API.

### 📁 **controller**
Contém os controladores responsáveis por expor os endpoints da API.

- **AlunoController**: Controlador que gerencia as operações relacionadas aos alunos.
  - Criar aluno
  - Listar alunos
  - Buscar aluno por ID
  - Deletar aluno por ID
  - Atualizar informações do aluno
- **DisciplinaController**: Controlador para operações relacionadas às disciplinas.
  - Criar disciplina
  - Listar disciplinas
  - Buscar disciplina por ID
  - Deletar disciplina por ID
  - Atualizar informações da disciplina
- **MatriculaAlunoController**: Controlador para operações de matrícula.
  - Criar matrícula
  - Trancar matrícula
  - Atualizar notas
  - Exibir histórico do aluno
- **ProfessorController**: Controlador para operações relacionadas aos professores.
  - Criar professor
  - Listar professores
  - Buscar professor por ID
  - Deletar professor por ID
  - Atualizar informações do professor

### 📁 **dtos**
Contém os **Data Transfer Objects (DTOs)** que são usados para transferir dados entre as camadas do sistema.

- **AtualizarNotasRequest**: DTO utilizado para enviar as notas a serem atualizadas de um aluno em uma disciplina.
- **DisciplinasAlunoResponse**: DTO que representa as disciplinas matriculadas por um aluno, incluindo informações como nome, professor, notas e status.
- **HistoricoAlunoResponse**: DTO que representa o histórico acadêmico de um aluno, exibindo todas as disciplinas cursadas e as respectivas notas.

### 📁 **enums**
Contém as enumerações utilizadas no sistema, representando categorias ou estados.

- **MatriculaAlunoStatusEnum**: Enum que define os status possíveis de uma matrícula de aluno:
  - **MATRICULADO**: O aluno está matriculado na disciplina.
  - **TRANCADO**: O aluno trancou a matrícula na disciplina.
  - **APROVADO**: O aluno foi aprovado na disciplina.
  - **REPROVADO**: O aluno foi reprovado na disciplina.

### 📁 **model**
Contém as entidades que representam os dados principais do sistema.

- **Aluno**: Representa a entidade de aluno no sistema.
- **Disciplina**: Representa uma disciplina oferecida pela instituição.
- **MatriculaAluno**: Representa a matrícula de um aluno em uma disciplina.
- **Professor**: Representa a entidade de um professor no sistema.

### 📁 **repository**
Contém os repositórios responsáveis pelas operações de banco de dados.

- **AlunoRepository**: Repositório para as operações relacionadas aos alunos.
- **DisciplinaRepository**: Repositório para as operações relacionadas às disciplinas.
- **MatriculaAlunoRepository**: Repositório para as operações relacionadas às matrículas dos alunos.
- **ProfessorRepository**: Repositório para as operações relacionadas aos professores.

### 📁 **service**
Contém as classes de serviço, responsáveis pela lógica de negócio do sistema.

- **AlunoService**: Contém a lógica de negócio para gerenciar alunos.
- **DisciplinaService**: Contém a lógica de negócio para gerenciar disciplinas.
- **MatriculaAlunoService**: Contém a lógica de negócio para gerenciar matrículas de alunos.
- **ProfessorService**: Contém a lógica de negócio para gerenciar professores.



## Tecnologias Utilizadas

- **Spring Boot**: Framework para o desenvolvimento rápido de aplicações Java baseadas em microserviços, facilitando a criação e a configuração de aplicativos independentes com uma arquitetura robusta.
  
- **Spring Data JPA**: Facilita a interação com o banco de dados utilizando JPA (Java Persistence API), abstraindo a persistência e simplificando as operações de CRUD.
  
- **Spring Web**: Módulo do Spring que facilita a criação de aplicações web, incluindo RESTful APIs, com suporte a controle de requisições HTTP, segurança, validação, entre outros.

- **SQL Driver**: Utilizado para a comunicação com bancos de dados relacionais. No caso deste projeto, o banco de dados é configurado para ser **H2 Database** (um banco de dados em memória), ideal para testes rápidos e desenvolvimento. O banco pode ser substituído por outros sistemas de banco de dados relacionais, como **MySQL** ou **PostgreSQL**, dependendo da necessidade do ambiente de produção.

- **Swagger**: Ferramenta para gerar documentação interativa da API, facilitando a visualização e o teste das funcionalidades disponíveis na API.

- **Lombok**: Biblioteca que reduz o código boilerplate (como getters, setters e construtores), gerando automaticamente esses métodos, melhorando a legibilidade e a manutenção do código.

 



## Operações Disponíveis

### **Aluno**

- **Criar aluno**: Adiciona um novo aluno ao sistema.
- **Listar alunos**: Retorna uma lista de todos os alunos cadastrados.
- **Buscar aluno por ID**: Permite buscar um aluno pelo seu ID único.
- **Deletar aluno por ID**: Permite excluir um aluno do sistema pelo ID.
- **Atualizar aluno**: Permite atualizar as informações de um aluno existente.

### **Professor**

- **Criar professor**: Adiciona um novo professor ao sistema.
- **Listar professores**: Retorna uma lista de todos os professores cadastrados.
- **Buscar professor por ID**: Permite buscar um professor pelo seu ID único.
- **Deletar professor por ID**: Permite excluir um professor do sistema pelo ID.
- **Atualizar professor**: Permite atualizar as informações de um professor existente.

### **Disciplina**

- **Criar disciplina**: Adiciona uma nova disciplina ao sistema.
- **Listar disciplinas**: Retorna uma lista de todas as disciplinas cadastradas.
- **Buscar disciplina por ID**: Permite buscar uma disciplina pelo seu ID único.
- **Deletar disciplina por ID**: Permite excluir uma disciplina do sistema pelo ID.
- **Atualizar disciplina**: Permite atualizar as informações de uma disciplina existente.

### **Matrícula**

- **Criar matrícula**: Matricula um aluno em uma disciplina.
- **Trancar matrícula**: Permite trancar a matrícula de um aluno em uma disciplina. Só pode ser feito se o status do aluno for `MATRICULADO`.
- **Atualizar notas**: Permite atualizar as notas de um aluno em uma disciplina.
- **Exibir histórico**: Exibe o histórico completo de disciplinas de um aluno, incluindo notas e status de matrícula.

## Como Executar

### Pré-requisitos

- **Java 11 ou superior**
- **Maven** (ou Gradle)

### Passos

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/seu-usuario/nome-do-repositorio.git
   ```

2. **Navegue até o diretório do projeto**:
   ```bash
   cd nome-do-repositorio
   ```

3. **Execute o projeto**:
   ```bash
   mvn spring-boot:run
   ```

4. **Acesse a API**:
   A API estará disponível em `http://localhost:8080`.

   Para acessar a documentação interativa gerada pelo Swagger, vá até `http://localhost:8080/swagger-ui.html`.

## Licença

Este projeto está licenciado sob a licença **MIT**. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

---

Este modelo de `README.md` é agora mais detalhado e inclui as operações principais do sistema conforme descrito. Se precisar de mais ajustes ou informações adicionais, é só me avisar!
