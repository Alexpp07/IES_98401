# IES_98401


## LAB 1


### lab1_2

O Maven é uma ferramenta de construção Java, que coordena as várias de construção de um projeto, tais como a obtenção de dependências, compilação do código fonte, testes, produção de binários, atualização da documentação ou mesmo instalação no servidor. Pode ser manipulado através da linha de comandos ou de qualquer IDE.

Confirmar a instalação do Maven:
    ```bash
    $ mvn --version
    ```

Criação de um projeto (executa-se o comando `mvn`, seguido do *plugin* `archetype` e do objetivo `generate`):
    ```bash
    $ mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
    ```
**archetype** é o protótipo a utilizar na criação do projeto, sendo disponibilizados vários desde os mais simples a complexos. Por defeito, o instalado é o `org.apache.maven.archetypes:maven-archetype-quickstart`, pelo que nos casos da sua utilização este pode ser ignorado no comando.

**groupId** é um identificador global do projeto. Deve começar com o inverso do nome do domínio controlado. ([Regras](https://docs.oracle.com/javase/specs/jls/se6/html/packages.html#7.7))

**artifactId** é o nome do jar sem a versão associada.

**version** é a versão do projeto. A versão inicial deve ser 1.0-SNAPSHOT.

O Diretório do projeto começa por ter um ficheiro **pom.xml**, onde o projeto é descrito, uma pasta **src** que contém todo o código fonte do projeto e a pasta **target**, onde é armazenada a saída da construção do mesmo.

A informação do projeto é discriminada no ficheiro **pom.xml**, onde para além dos dados escritos por defeito na construção do projeto, podem ser adicionados detalhes adicionais, como licenças ou a constituição da equipa.

Quase todos os projetos de *software* desenvolvidos fazem recurso de ferramentas externas. O Maven permite de forma muito simples a integração de bibliotecas externas credíveis, disponibilizadas através de um repositórios oficiais (exemplo do Retrofit e do Gson).

O uso destes recursos externos dá origem a **dependências**. Para as adicionar só temos de criar um marcador `<dependency>` dentro do marcador `<project><dependencies>` no ficheiro **pom.xml**.

O protótipo utilizado para criar o projeto terá duas classes criadas: uma na pasta **src/main** e outra na **srt/test**. Para testarmos que o projeto foi construído sem problemas, podem executá-lo através do terminal.

Compilação:
    ```bash
    $ mvn package
    ```

Execução:
    ```bash
    $ mvn exec:java -Dexec.mainClass="..MainClassName.."
    ```

Ao executar o projeto é possível passar argumentos através do terminal. Ao executar, temos de utilizar:
    ```bash
    $ mvn exec:java -Dexec.mainClass="..MainClassName.." -Dexec.args="<arg1> <arg2> <arg3>"
    ```

### lab1_3