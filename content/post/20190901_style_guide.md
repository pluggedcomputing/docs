---
title: Integração Prettier + ESLint + Airbnb Style Guide + EditorConfig no VSCode
date: 2019-09-01
---

Nesse guia vamos te ajudar a configurar algumas bibliotecas e estrenções que vão te ajudar na hora de padronizar e organizar o codigo dos seus projeto.

> Como referencia, utilizamos o Visual Studio Code como IDE e o Yarn para instalar as dependencia.

## Ferramentas

### ESLint ![ESLint](https://freeicons.io/laravel/public/uploads/icons/png/11436511531536298177-128.png)

ESLint , é um programa que percorre seu código e o analisa quanto a possíveis erros. A extensão é altamente configurável, com uma variedade de opções internas para combinar com o guia de estilo da sua empresa. Ele pode destacar erros enquanto você digita seu editor, além de exibir uma lista detalhada de erros no seu console.

### Prettier ![Prettier](https://freeicons.io/laravel/public/uploads/icons/png/11490474241551942136-128.png)

Muitas vezes não escrevemos o código mais bonito, mas com o Prettier não é preciso mais se preocupar com isso. Após uma longa sessão de desenvolvimento, é só salvar seu arquivo e depois **puf** ele formata magicamente o código automaticamente!

![dif](https://miro.medium.com/max/1420/1*BTj6MICTzE_q8vdtgv_b5w.gif)

### EditorConfig ![EditorConfig](https://editorconfig.org/logo.png)

O EditorConfig ajuda a manter estilos de codificação consistentes para vários desenvolvedores que trabalham no mesmo projeto em vários editores e IDEs. O projeto EditorConfig consiste em um formato de arquivo para definir estilos de codificação e uma coleção de plugins de editor de texto que permitem aos editores ler o formato do arquivo e aderir aos estilos definidos. Os arquivos EditorConfig são facilmente legíveis e funcionam bem com os sistemas de controle de versão.

## Configurando no VSCode

1. No VSCode, baixe as extensões: [ESLint](https://github.com/Microsoft/vscode-eslint.git), [Prettier](https://github.com/prettier/prettier-vscode) e [EditorConfig](https://github.com/editorconfig/editorconfig-vscode).
2. Instale as bibliotecas **ESLint** e **Prettier** no seu projeto. Para isso, no diretório raiz do seu projeto, execute:

`> yarn add --dev eslint prettier`

3. Instale a configuração do [Airbnb](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb). Se você estiver usando o **npm 5+**, poderá executar este atalho para instalar a configuração e todas as suas dependências:

`> npx install-peerdeps --dev eslint-config-airbnb`

4. Instale [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) (desativa a formatação para ESLint) e [eslint-plugin-prettier](github.com/prettier/eslint-plugin-prettier) (permite que o ESLint mostre erros de formatação enquanto digitamos)

`> yarn add --dev eslint-config-prettier eslint-plugin-prettier`

5. Crie um arquivo **.eslintrc.json** no diretório raiz do seu projeto:

```
{
  "extends": ["airbnb", "prettier"],
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": ["error"]
  },
}
```

6. O proximo passo é garantir que a formatação do Prettier seja feita ao falvar um arquiivo. Insira **_"editor.formatOnSave": true_** nas configurações do usuário no VSCode.

> Para abrir as configurações de usuario, use o atalho `Ctrl + Shift + P` e busque por: "_Preferences: Open Settings (JSON)_"

7. Crie um arquivo **.editorconfig** no diretório raiz do seu projeto:

```yml
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = false
```

**Parabéns, você conseguiu!**

Seguindo todos esse passos, o seu VSCode deve esta pronto para detectar erros mais cedo, e junto com os formatadores ajudará a manter a consistência em todo o codigo fonte. Com essas extensões trabalhando lado a lado, será possivel criar um código limpo e sustentável. Seu chefe e seus colegas vão te agradecer.

## Referencias

Integrating Prettier + ESLint + Airbnb Style Guide in VSCode. (20180). Disponivel em: <https://blog.echobind.com/integrating-prettier-eslint-airbnb-style-guide-in-vscode-47f07b5d7d6a>.
