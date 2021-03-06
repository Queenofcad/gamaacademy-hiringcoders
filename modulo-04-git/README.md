# Módulo 4 - GIT

**GIT** é um sistema de controle de versão distribuído, ou seja, você consegue ter o seu código fonte em diversos computadores para compartilhar o desenvolvimento.

Foi criado por *Linus Torvald* (criador do Linux) para melhorar a performance do time de desenvolvimento do Linux.
___
## Por que falamos de versionamento?

- Sistema descentralizado de versionamento de código
- É amplamente utilizado por desenvolvedores

### Principais Ferramentas do Mercado

- Github
- Bitbucket
- Gitlab

___
## Init, Add, Commit?

- **git init** -> Inicializa o versionamento do repositório GIT
- **git add** nome_do_arquivo -> Sinaliza ao GIT que ele deve monitorar os arquivos
- **git commit -m** "mensagem" -> Cria um ponto na linha do tempo do repositório com uma mensagem sobre a alteração realizada
- **git commit -am** "mensagem" -> Atalho para **git add** + **git commit -m**

___
## Log, Status, Show?

- **git log** -> Visualiza informações de histórico sobre os commits na linha do tempo
- **git status** -> Informa o status do repositório local atual (branch) e arquivos que sofreram alterações em relação ao último commit
- **git show** id_do_commit -> Inspeciona um commit específico

___
## Branch?

É uma ramificação de uma linha temporal. A partir da Branch Master, que é a linha do tempo principal com todos os commits, conseguimos criar novas Branches em paralelo.

A finalidade disso é proteger a Master e dar mais autonomia e liberdade para o desenvolvedor que está trabalhando em uma nova funcionalidade, melhoria ou versão. Ele cria a sua própria Branch de desenvolvimento.

É uma boa prática categorizar as Branches pois existem diversos tipos de linhas do tempo, cada qual com suas características próprias. Por exemplo:

- master
- develop
- feature
- release
- hotfix

___
## git branch
Para criar uma nova Branch utilizamos o seguinte comando:

    git branch nome_da_categoria/nome_da_branch

Por exemplo:

    git branch feature/lista-clientes

Utilizando apenas **git branch** uma lista contendo todas as Branches do projeto é exibida.
___
Para remover uma Branch usamos:

    git branch -D nome_da_categoria/nome_da_branch
___
## git checkout
Para alternar de uma Branch para a outra, usamos o seguinte comando:

    git checkout nome_da_categoria/nome_da_branch

Por exemplo:

    git checkout feature/lista-clientes

Podemos ainda, caso a Branch ainda não esteja criada, utilizar:

    git checkout -b nome_da_categoria/nome_da_branch

Dessa forma, o GIT criará a Branch e já irá migrar para ela.

Também é possível "voltar no tempo" usando:

    git checkout id_do_commit

**Atenção**: Todas as alterações realizadas posteriormente a esse commit serão ignoradas.
___
## git reset
Para remover os arquivos da Stage ("tirar" o git add) usamos o comando:

    git reset
___
## git merge
Para juntar Branches usamos:

    git merge nome_da_categoria/nome_da_branch

Por exemplo:

Criamos a Branch **feature/lista-clientes**, agora, queremos trazer todas as alterações realizadas nessa Branch para a Master. Seguimos os seguintes passos:

1. **git checkout master** -> Para ir para a Branch Master
2. **git merge feature/teste-nova-branch**

Nesse momento todas as alterações realizadas na Branch **feature/teste-nova-branch** como criação de novos arquivos, ou alterações nos arquivos existentes, estarão na Master e podemos comprovar isso se utilizarmos o comando **git log** pois teremos o log contendo os commits realizados na Branch **feature/teste-nova-branch** juntamente com os commits já realizados anteriormente na Master.

___
Interessante:

Ao executar o **git merge** o GIT automaticamente faz o update dos arquivos e cria um commit sobre isso, deixando registrado na linha do tempo.

___
## Clone e Pull?

- **git clone** -> Clona um projeto de um repositório remoto
- **git pull** -> Atualiza o repositório local a partir do repositório remoto

___
## .gitignore

O **.gitignore** é um arquivo que lista todos os arquivos e diretórios que devem ser **ignorados** pelo GIT em relação ao monitoriamento. 

Esses arquivos e pastas deverão ser selecionados e incluídos nessa lista pelo desenvolvedor, para atender suas necessidades mediante cada projeto.

___
## Pull Request

**Pull Request** é uma solicitação de um **pull** em um repositório ao qual você gostaria de contribuir. Serve principalmente para contribuição de código de projetos open source.

### Como fazer um Pull Request?

1. Vá até o repositório desejado e faça um **fork** para o seu repositório

    <img src="fork.png">

2. Faça um **clone** do repositório remoto para o seu repositório local

    <img src="clone.png">

        git clone https://github.com/khayan/gama-no-pullrequest.git

3. Crie uma **nova branch** para trabalhar suas alterações

        git checkout -b feature/nova-feature

4. Faça as alterações necessárias
5. **Commit** as alterações

        git commit -am "Sugestões para nova feature"

6. Faça um **push**

        git push --set-upstream origin feature/nova-feature

7. Vá até o **repositório forkado** e faça o **Pull Request**! 

    <img src="pull-request.png">
    <img src="pull-request-compare.png">

___
## Gitflow

É uma das metodologias mais utilizadas no versionamento de código entre times.

- **Master** -> branch principal do projeto. Código oficial e poderia estar em produção
- **Hotfix** -> branch para ajuste de pequenos bugs que eventualmente foram percebidos depois do código ter sido colocado na Master
- **Release** -> branch de funcionalidades desenvolvidas e testadas que formam um pacote para ser submetido a Master posteriormente
- **Develop** -> branch de homologação, testes e controle. A partir dela são criadas branches de features e correção de bugs
- **Feature** -> branch de desenvolvimento de funcionalidades para o software
- **Bugs** -> branch para correção de erros de features que foram para a develop mas eventualmente voltaram por conter problemas

É interessante ter essa divisão de camadas de branches para evitar alterações que quebrem o código, gerem retrabalho ou problemas ainda mais complicados.

<img src="gitflow.png">
