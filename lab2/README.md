# IES_98401

Lab2 by Alexandre Pereira Pinto

## LAB 2

### lab2_1

Docker Containers são usados para providenciar tempos de execução virtualizados para qualquer tipo de serviços; Os Servlet Containers são usados para providenciar um tempo de execução para executar código Java "web-related" e "server-sided", ou seja, não há virtualização. As funções do Servlet Container podem ser divididas em 6 objetivos:

Servidor Web recebe pedido HTTP;
Servidor Web encaminha o pedido para um servlet container;
O servlet é recuperado dinamicamente e carregado no espaço de endereço do container, se não estiver no container;
O container invoca o método init() do servlet para inicialização;
O container invoca o método service() do servlet para processar a solicitação HTTP, ou seja, ler os dados na solicitação e formular uma resposta. O servlet permanece no espaço de endereço do container e pode processar outras solicitações HTTP.
O servidor Web retorna os resultados gerados dinamicamente para o local correto.

Folder do Apache-Tomcat: home/apache-tomcat-9.0.54
User: admin | Password: admin

Para criar uma Web Application baseado em Maven através de um terminal:
    ```bash
    $ mvn archetype:generate DgroupId=org.codehaus.mojo.archetypes -DartifactId=webapp-javaee7 DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.1 DinteractiveMode=false
    ```

Para obtermos dados do URL podemos: String user = request.getParameter("username");

Para implementar um runtime error (NullPointerException): if(user == null){ throw new NullPointerException("Username not found!"); }

Caso o user não exista o error é triggered e é imprimida uma mensagem a dizer que o utilizador não foi encontrado;


### lab2_2
O Jetty pode ser executado no modo "embedded". Isto significa que não é necessário construir um ficheiro WAR e lançá-lo no servidor Jetty "solitário".


### lab2_3

Uma vez criado o projeto, este deve ser testado.

Para tal, primeiro compila-se:
    ```bash
    $ mvn install #Este comando deve ser utilizado na primeira compilação e sempre que são adicionadas dependências
    $ mvn clean package #Usar só para compilação
    $ mvn install -DskipTests && java -jar target\webapp1-0.0.1-SNAPSHOT.jar # (Ou: $ ./mvnw spring-boot:run) Para correr o programa
    ```
Resultado de aceder a http://localhost:8080/ após corer o Spring Boot:

Whitelabel Error Page

This application has no explicit mapping for /error, so you are seeing this as a fallback. Fri Oct 29 21:58:40 WEST 2021 There was an unexpected error (type=Not Found, status=404).

**`@SpringBootApplication`** Identifica a classe base do projeto, aplicando as configurações por defeito.
**`@Controller`** Esta anotação indica que uma classe gere pedidos HTTP. Abstrai o programador de extender classes base ou de fazer qualquer referência à API do Servlet.
**`@RequestMapping`**  Esta anotação associa um tipo de pedido HTTP ao método que o vai processar. O método por sua vez pode ter várias assinaturas, não só ao nível dos argumentos como do valor de retorno.
**`@RequestParam`** e **`@RequestBody`** Permitem mapear parâmetros do pedido HTTP para objetos que permitam a sua manipulação no código.

O método main () usa o método SpringApplication.run () do Spring Boot para iniciar uma aplicação.

Mudou-se a porta a usar de modo a não entrar em conflito com a porta usada na alínea anterior. Para tal, editou-se o ficheiro application.properties (src/main/resources): server.port = 9000

A aplicação web que estamos a contruir é 100% Java, não requer nenhum ficheiro do tipo .xml

Após correr a aplicação com ./mvnw spring-boot:run (ou correndo o programa principal em qualquer IDE), acedeu-se ao site: http://localhost:9000/greeting onde foi apresentada uma página em branco e com a mensagem "Hello, World!"

Caso se adicione um parâmetro "name" ao site (http://localhost:9000/greeting?name=User) a mensagem "Hello,World!" muda para "Hello,User!". Isto comprova que o @RequestParam está a funcionar corretamente.


### lab2_4
Criei a classe representativa "Quotes.java" que recebe como argumentos o id, show e quote, assim como os seus contrutores e métodos get. Depois criei um controlador, "QuotesController.java" de forma a lidar com os GET requests de acordo com o url especificado: - /api/quotes - retorna uma quote aleatória de uma série aleatória - api/quotes?show=<show_id> - retorna uma quote aleatória de uma série específica - api/shows - lista de todas as séries que existem Criei um ArrayList para cada série e suas respetivas quotes e um HashMap "quotes" para guardar essas informações.


### Review Questions

A. Uma Java **Servlet** é uma classe que corre no servidor e tem a função de receber, processar e responder aos pedidos do cliente. O *servlet container* é um componente do servidor responsável pela gestão dos pedidos que permite a geração de páginas dinâmicas. Este é então responsável por receber os pedidos do cliente, converte-los em chamadas às classes Java que implementam a classe Servlet e receber as respostas destas classes que depois encaminha para o cliente. É ainda responsável pela gestão da concorrência, permitindo o processamento de múltiplos pedidos em simultâneo.

B. O Spring usa MVC (Model, View, Controller) para servir o conteúdo da web:
-> O modelo é a camada lógica da aplicação. O framework Spring possui o org.springframework.ui.Model que permite mapear atributos para serem posteriormente renderizados nas visualizações.
-> A visualização é a camada "front-end" e geralmente é armazenada na pasta de modelos de um projeto Spring
-> O controlador aceita inputs e converte-os em comandos para o modelo ou vista. Spring tem uma anotação especial para designar uma classe como um Controlador.


C. As dependências iniciais permitem simplificar a construção do sistema, padronizando alguns aspectos do mesmo.

D. **`@SpringBootApplication`** identifica a classe base do projeto, aplicando as configurações por defeito. ESta anotação adiciona:
-> @ComponentScan: Ativa a pesquisa pelas classes componente. Diz ao Spring para procurar outros componentes, configurações e serviços no pacote *com/example*, permitindo que ele encontre os controladores.
-> @Configuration: Permite o registo de componentes da aplicação adicionais e importa classes de configuração. Marca a classe como uma fonte de definições de bean para o contexto da aplicação.
-> @EnableAutoConfiguration: Ativa o mecanismo de configuração automática com base nos ficheiros jar gerados.Diz ao Spring Boot para começar a adicionar beans com base nas configurações do classpath, outros beans e várias configurações de propriedade.

E.
-> Utilizar a linguaguem JSON para comunicar pois é de fácil leitura e compacta. Esta é uma das linguaguens mais conhecidas e utilizadas;
-> Ter várias versões de uma API. Uma vez que estamos em constante desenvolvimento, é seguro ter diferentes versões para que não hajam problemas no futuro com atualizações;
-> Retornar detalhes de erros no JSON ou na resposta para que seja mais fácil para o utilizador fazer o seu debug;
-> Utilizar dados em cache, em memória local, para que seja mais rápido obter a informação pretendida. Assim, não será necessário consultar sempre a base de dados;
-> Limitar o aninhamento na REST API