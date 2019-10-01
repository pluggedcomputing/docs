---
title: Como contribuir?
subtitle: Guia de como utilizar uma organização baseada no git-flow para contribuir com o projeto
comments: false
date: 2019-08-28
---
Aqui entraremos mais fundo no mundo do git. Para isso, é necessario que você tenha dominio basico dos comandos da ferramanta. Deixo aqui a sujestão de um [Guia Pratico](https://rogerdudler.github.io/git-guide/index.pt_BR.html) de Git para você não ter complicações.

Em nosso projeto, utilizamos adaptações da metodologia do git-flow. O git-flow é um conjunto de extensões para o git que provê operações de alto-nível para repositórios usando o modelo de branches do Vincent Driessen. [Saiba mais](https://nvie.com/posts/a-successful-git-branching-model/)

### Núcleo

No núcleo, o modelo de desenvolvimento é muito inspirado nos modelos existentes. 
O repositório central possui dois ramos principais com uma vida útil infinita:

   * **_master_**
      * Consideramos origin/master o ramo principal onde o código fonte HEAD sempre reflete um estado pronto para produção.

   * **_develop_**
      * Consideramos origin/develop o ramo principal em que o código-fonte HEAD sempre reflete um estado com as últimas alterações de desenvolvimento entregues para a próxima versão. Alguns chamariam isso de "ramo de integração". É aqui que todas as compilações noturnas automáticas são criadas.

![branchs](https://nvie.com/img/main-branches@2x.png)

### Realizando alterações

O desenvolvimento de novas funcionalidades e correção de bugs começa na branch 'develop'.
Por isso, lembre-se sempre de atualizar a branch 'develop'. Para isso execute os comandos: 

```
> git checkout develop \\ Caso esteja em outra branch
> git pull origin develop \\ Atualizando a branch develop
```

#### Funcionalidades/features

Comece o desenvolvimento de uma nova funcionalidade com:

`> git checkout -b feature/MYFEATURE develop"`

Esse comando cria um novo branch da funcionalidade baseado no 'develop' e alterna para ele.

#### Correção de Bugs/bugfix

Para começar, utilize o comando:

`> git checkout -b bugfix/MYBUG develop"`

Esse comando cria um novo branch da funcionalidade baseado no 'develop' e alterna para ele.

### Finalizando alterações

Após todas as suas alterações terem sido realizadas e devidade commitadas, você deve enviar as suas alterações para o repositorio remoto no GitLab.

`> git push origin SUABRANCH`

> Certifique-se sempre de que suas mudanças estão corretas seguem todos os padrões de desenvolvimento e boas praticas adotados no projeto.