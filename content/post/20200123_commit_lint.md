---
title: Padronização das mensagens de commit
date: 2020-01-23
---
Visando obter uma alta qualidade e padronização das mensagem dos commits, em nosso projeto, utilizamos o [commit-lint](), que ajuda na padronização das mensagens de commit logo quando elas são criadas.

Em nosso projeto, utilizamos o [conventional commit format](https://www.conventionalcommits.org/en/v1.0.0/), baseado no [Angular convention](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional#type-enum).

De modo geral, o padrão é da seguinte forma:

`type(scope): subject`

onde:

`type`: pode assumir os seguintes valores:

| **Valor** | **Descrição**                                                    |
| --------- | ---------------------------------------------------------------- |
| build     | commites que disparam builds                                     |
| ci        | commites para configuração de integração continua                |
| chore     | commites referentes a tarefas de gestao de projeto               |
| docs      | commites referentes a algum tipo de documentação                 |
| feat      | commites de novas features                                       |
| fix       | commites para correção de bugs em desenvolvimento ou em produção |
| perf      | commites relacionados a performace do codigo e/ou da aplicação   |
| refactor  | commites de refatoração de codigo                                |
| revert    | commites para reverter alguma alteração no codigo                |
| style     | commites para alterações na formatação do codigo, sem alteracoes no codigo        |
| test      | commits para adição/atualização de scripts de teste              |

`scope`: deve ser o sufixo da branch que é o mesmo id do issue da alteração.
> ex: *develop* ou *#10* 

`subject`: é a mensagem do commit, deve ser curta e objetiva, apontando exatamente a alteração realizada. 

Uma mensagem de commit ideal, utilizando esse padrão, seria:

*`feat(#01): initial commit`*

Para mais informações, consulte a documentação do [commit-lint](https://github.com/conventional-changelog/commitlint#config).
