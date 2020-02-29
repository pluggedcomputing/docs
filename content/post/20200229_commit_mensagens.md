---
title: Como escrever mensagens de commits no Git
date: 2020-02-29
---
> Esse texto é uma adaptação de https://www.lucascaton.com.br/2017/10/16/como-escrever-mensagens-de-commits-no-git/

Devemos escrever a mensagem no presente? No futuro? Em português? Em inglês? São infinitas as formas as quais uma mensagem de commit pode ser escrita.

Sabemos que o ingles é fundamental na nossa profissão e existem inumeras [vantagens de se programar em ingles](https://www.lucascaton.com.br/2015/05/22/8-motivos-pra-programar-em-ingles/). Porém no nosso projeto, apenas o codigo é obrigatorio ser em ingles, as mensagens de commit são livres de indiomas e você pode escolher o que preferir. Remendamos que faça em português mesmo. 

Apesar de a maioria dos desenvolvedores escrever boas mensagens, não podemos generalizar: sempre tem alguém para provar que a zueira não tem limites estragar a estatística.

![imagem](https://www.lucascaton.com.br/assets/images/2017/10/git-commits-messages.png)

### Por que uma boa mensagem importa?

Alguns motivos:

* Caso um bug seja introduzido, uma boa mensagem de commit facilita a identificação de onde/quando isso aconteceu;
* Se você reverter um commit, a mensagem será Revert "mensagem original", deixando claro o que está sendo revertido;
* Boas mensagens se tornam útias ao exibir listas de commits através de comandos como git blame, git log, git shortlog, etc;
* Facilita a criação de changelog automatico;
  
### Como escrever boas mensagens?

O correto é escrever na forma imperativa. Ou seja, a sua mensagem precisa sempre estar apta a completar a seguinte frase:  
“Se aplicado, esse commit vai **seu resumo aqui**”

### Exemplos: 

✅ Se aplicado, esse commit vai **Refatorar o subsistema X para facilitar a leitura**  
✅ Se aplicado, esse commit vai **Atualizar a documentação de introdução**  
✅ Se aplicado, esse commit vai **Remover métodos obsoletos**  
✅ Se aplicado, esse commit vai **Release version 1.0.0**  
✅ Se aplicado, esse commit vai **Mesclar solicitação de recebimento nº 123 do usuário / filial**  

Note como isso não fica legal escrevendo de forma não-imperativa:

❌ Se aplicado, esse commit vai **Corrigido o erro com Y**   
❌ Se aplicado, esse commit vai **Mudando o comportamento de X**  
❌ Se aplicado, esse commit vai **Mais correções para coisas quebradas**  
❌ Se aplicado, esse commit vai **Novos métodos API agradáveis**

> Não é preciso adicionar um ponto no final da mensagem.

Além de mensagens boas e intuitivas, é precisso seguir o padrão de commit do nosso projeto.

Acesse: [Padronização das mensagens de commit](https://pluggedcomputing.gitlab.io/post/20200123_commit_lint/)


