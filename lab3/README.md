# IES_98401

Lab3 by Alexandre Pereira Pinto

## LAB 3

### lab3_1

a)
Fazemos a anotação de User como @Entity para que seja possível fazer operações CRUD ao domínio das entidades. Isto é feito com Hibernate, uma implementação JPA.
Utilizando o @NotBlanck atrás dos campos do name e do email, é possível fazer a sua validação antes de atualizar ou alterar a entidade na base de dados. Isto é feito através do Hibernate Validator.
Spring Data JPA permite implementar repositórios (JPA-based repositories).

-> showSignUpForm() -
-> addUser() - 
-> showUserList() - 
-> showUpdateForm() -
-> updateUser() - 
-> deleteUser() - 

b) 
A instância do novo repositório é feita

Os métodos invocados em userRepository pelo UserController são:
-> save() - para guardar novos dados no repositório;
-> findAll() - para encontrar todos os dados do repositório;
-> findById() - para encontrar todos os dados correspondentes àquele Id do repositório;
-> delete() - para eliminar dados do repositório;
Estes métodos estão definidos em CrudRepository pois o UserRepository é uma extensão dessa classe.

Os dados são guardados numa base de dados relacional.

Através da utilização de anotações @NotBlanck na classe User, é feita a verificação do campo email address para que este não esteja vazio. 

c)
Para adicionar um novo campo na entidade User, tivemos de adicionar novos métodos para o novo atributo phoneNumber (o número de telemóvel). Utilizámos métodos semelhantes aos dos outros atributos.
Relativamente às páginas .html, adicionámos novos campos para ser possível introduzir o número de telemóvel ao adicionar e atualizar os dados de um utilizador.


### lab3_2

### lab3_3