# IES_98401

Lab3 by Alexandre Pereira Pinto

## LAB 3

### lab3_1

a)
Fazemos a anotação de User como @Entity para que seja possível fazer operações CRUD ao domínio das entidades. Isto é feito com Hibernate, uma implementação JPA.
Utilizando o @NotBlanck atrás dos campos do name e do email, é possível fazer a sua validação antes de atualizar ou alterar a entidade na base de dados. Isto é feito através do Hibernate Validator.
Spring Data JPA permite implementar repositórios (JPA-based repositories).

-> showSignUpForm() - mostrar o formulário de registo;
-> addUser() - adiciona novo utilizador à base de dados após validar os campos 'restritos' (name e fields);
-> showUserList() - mostra a lista de utilizadores;
-> showUpdateForm() - relaciona a entidade User que dá match com o id da base de dados;
-> updateUser() - atualiza a entidade na base de dados;
-> deleteUser() - elimina a entidade da base de dados;

b) 
A instância do novo repositório é feita através da anotação "@Autowired", que insere uma instância do UserRepository no objeto do UserController

Os métodos invocados em userRepository pelo UserController são:
-> save() - para guardar novos dados no repositório;
-> findAll() - para encontrar todos os dados do repositório;
-> findById() - para encontrar todos os dados correspondentes àquele Id do repositório;
-> delete() - para eliminar dados do repositório;
Estes métodos estão definidos em CrudRepository pois o UserRepository é uma extensão dessa classe.

Os dados são guardados numa base de dados relacional. Usamos a h2database, que foi adicionada ao projeto como sendo uma dependência.

Através da utilização de anotações @NotBlanck na classe User, é feita a verificação do campo email address para que este não esteja vazio. 

c)
Para adicionar um novo campo na entidade User, tivemos de adicionar novos métodos para o novo atributo phoneNumber (o número de telemóvel). Utilizámos métodos semelhantes aos dos outros atributos.
Relativamente às páginas .html, adicionámos novos campos para ser possível introduzir o número de telemóvel ao adicionar e atualizar os dados de um utilizador.


### lab3_2

Instalação do mysql no docker: sudo docker pull mysql

Criação de docker container $ docker run --name mysql5 -e MYSQL_ROOT_PASSWORD=secret1 -e MYSQL_DATABASE=demo -e MYSQL_USER=demo -e MYSQL_PASSWORD=secret2 -p 33060:3306 -d mysql/mysql-server:5.7

Criou-se um projeto Maven tal como os anteriores, mas com as seguintes dependências: Web, JPA, DevTools, MySQL and Validation.

Adicionou-se ao ficheiro application.properties:
 (comment) MySQL spring.datasource.url=jdbc:mysql://127.0.0.1:33060/demo 
spring.datasource.username=demo 
spring.datasource.password=secret2 
spring.jpa.database-platform=org.hibernate.dialect.MySQL5InnoDBDialect 
 (comment) Strategy to auto update the schemas (create, create-drop, validate, update) 
spring.jpa.hibernate.ddl-auto = update

Alterou-se o ficheiro EmployeeRepository para que fosse possível pesquisar através do email.


### lab3_3

Não consegui realizar esta parte do guião toda. Criar o projeto maven com as dependências necessárias. Criei também algumas pastas e ficheiros para começar a fazer a web application, alterei o ficheiro pom.xml e ainda um Dockerfile.dockerfile.


### Review Questions

A. Enquanto que o @Controller corresponde aos controladores MVC, o @RestController é uma combinação do @Controller e da anotação @ResponseBody.
O @Controller cria um Map of Model Object e procura uma view, por outro lado, o @RestController retorna dados de objetos e objetos gravados diretamente na resposta HTTP (JSON, XML...).

B.

C. 
-> @Table - Cria a tabela na base de dados da aplicação;
-> @Id - A variável transforma-se na coluna id da tabela da base de dados. É incrementado automaticamente;
-> @Columm - Permite que a variável se torne numa coluna na tabela da base de dados.

D. O @AutoWired foi usado na classe do Rest Controller visto que permite injetar a dependência do objeto implicitamente.
