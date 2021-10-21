# IES_98401

Lab1 by Alexandre Pereira Pinto

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

Para adicionar código a um repositório a partir de uma pasta já criada, não deve ser feito `git clone`, mas sim iniciado um repositório novo na pasta existente.

```bash
$ cd project_folder
$ git init
$ git remote add origin <REMOTE_URL>
$ git add .
$ git commit -m "Initial commit"
$ git push -u origin main
```

### lab1_4

O **Docker** é como que um Sistema Operativo *light* que corre sobre o nosso SO (virtualização ao nível do SO) e que permite de forma simples construir aplicações em *containers*. 

Um ***container*** não é mais do que <u>um processo em execução com algumas funcionalidades de encapsulamento que o isolam do anfitrião e dos restantes *containers*</u>. Cada um utiliza o seu sistema de ficheiros, providenciado por uma ***Docker Image***, que agrupa o seu próprio *software*, bibliotecas e arquivos de configuração.

***Dockerfile*** é um script de instruções a usar para criar uma container image.

Contrasta com as VM, que correm um SO virtual completo, consumindo muitos mais recursos do que os necessários para a aplicação que vão executar.

A organização em *containers* permite simplificar o processo de desenvolvimento e execução, oferecendo:

- **Flexibilidade**. Até as aplicações mais complexas podem ser colocadas num *container*;
- **Leveza**. <u>Partilham o núcleo, tornando-los muito mais eficientes do que as máquinas virtuais;</u>
- **Portabilidade**. Uma aplicação pode ser construída localmente, *deployed* na *cloud* e executada por todos;
- **Altamente desacoplado**. São sistemas maioritariamente fechados, podendo ser substituídos sem afetar os restantes.
- **Escalabilidade**. Podem ser aumentados e distribuídos;
- **Segurança**. Por defeito, impõem grandes restrições e isolamentos aos processos.

**Arquitetura Portainer** consiste em dois elementos: o Portainer Server e o Portainer Agent. Ambos são executados como containers leves num container já criado. O Portainer Agent deve ser enviado para todos os nós do cluster e configurado de forma a reportar para o container do Portainer Server.

### lab1_5

Importante: não esquecer de alterar as dependências.


## Review Questions

A)
O ciclo de vida padrão do Maven (***Maven Default***) tem várias fases diferentes, entre elas:
**validação** - são validadas as informações necessárias e se o projeto está correto;
**compilação** - compila-se o código fonte;
**teste** - são utilizadas estruturas de teste no código fonte;
**pacote** - criação de um ficheiro jar;
**verificação** - executar verificações nos resultados dos testes para garantir que os critérios são cumpridos;
**instalação** - instalar o pacote no repositório local e das suas dependências;
**entregar** - copia-se o pacote final para o repositório remoto para compartilhar com outros desenvolvedores e projetos.

O ***Maven clean*** é utilizado quando queremos remover os ficheiros gerados ao longo da construção da diretoria do projeto.

O ***Maven site*** é utilizado para gerar um site para o projeto.


B)
***Maven*** é uma ferramenta de construção cujo objetivo principal é configurar um projeto e lidar com as atividades de construção e artefatos resultantes. Pode ser usado para executar um projeto usando diferentes plug-ins para executar uma classe específica.


C)
```bash
git clone
git branch [modifications] 
git add .
git commit -m "COMMENTS"
git push
```


D)
Num projeto de equipa devemos escrever comentários de forma a que todos consigam perceber o que é que o novo código ou o código que foi alterado faz. Algumas "boas práticas" para melhorar estes comentários poderão ser:
- utilizar espaços em branco para separar diversas secções;
- explicar detalhadamente o código escrito;
- explicar qual foi o problema resolvido;
- explicar o porquê de ter feito daquelas mudanças;
- colocar o assunto em letra maiúscula;


E)
Os volumes do ***Docker*** são sistemas de arquivos montados em containers Docker para preservar os dados gerados pelo container em execução. Os volumes são armazenados no host, independente do ciclo de vida do container. Isso torna os dados seguros se um container for excluído e permite que os usuários façam backup dos dados e compartilhem sistemas de arquivos entre containers facilmente.