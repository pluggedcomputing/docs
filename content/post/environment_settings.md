---
title: Configurando Ambiente
date: 2019-09-25
---
### Pré Requisitos
Para configurar o ambiente para esse projeto, você vai precisar ter instalado alguns aplicativos:

1. Instale o Chocolatey e as demais dependências: [Baixar o chocolatey](https://chocolatey.org/docs/installation)
2. SDK Android (Android Studio download ou Command line tools only): [Baixar o SDK Android](https://developer.android.com/studio/#downloads)
3. JAVA JDK 8: [Baixar o JDK 8](https://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html)
4. Node JS: [Baixar o Node JS](https://nodejs.org/en/download/)
5. Git:  [Baixar o Git](https://git-scm.com/downloads)
6. Visual Studio Code: [Baixar o VS Code](https://code.visualstudio.com/download)
7. Yarn: [Baixar o Yarn](https://yarnpkg.com/lang/pt-br/docs/install/#windows-stable)

* Caso tenha baixado o Android Studio execute mais esses passos adicionais:
   1. Abra o Android Studio > SDK Manager > SDK Plataforms. Escolha uma versão do android do seu desejo. (Recomendamos a partir da 4.4 kitkat)
   2. Mude para aba de SDK Tools. Escolha:
      * Android SDK Build-Tools
      * Android Emulator
      * Android SDK Platform-Tools
      * Android SDK Tools
      * Intel x86 Emulator Accelerator (HAXM installer)
   3. Prescione **Aplicar**, espere o download e a instalação do SDK.
   
* Caso tenha optado pelo Command line tools only, basta extrair mover a pasta baixada para **C:\Users\<Seu Usuario>\AppData\Local\Android\sdk**
      
> A instalação do **Yarn** e do **Visual Studio Code** não não são obrigatorias, porém são altamente recomendadas.

### Configurando Variaveis de Ambiente

Os exemplos utilizados aqui serão baseados no **Windows 10**.   Caso seu sistema operacional seja Linux ou macOS, você pode consultar os seguintes tutoriais: [Linux](https://docs.rocketseat.dev/ambiente-react-native/android/linux#configurando-sdk-do-android-no-linux) | [macOS](https://docs.rocketseat.dev/ambiente-react-native/android/macos#configurando-sdk-do-android-no-macos)

#### Variaveis JAVA

1. Localize o diretório de instalação Java
>Se você não alterou o caminho durante a instalação, ele será parecido com isso **__C:\Program Files\Java\jdk1.8.0_65__**
2. Vá para **Painel de controle** > **Sistema** > **Configurações avançadas do sistema**
3. Clique no botão **Variáveis de ambiente**
4. Sob **Variáveis do sistema**, clique em **Novo**
5. No campo **Nome da variável** insira:
   * JAVA_HOME se você instalou o JDK (Kit de desenvolvimento Java)
6. No campo **Valor da variável**, insira o seu caminho da instalação do JDK (Passo 1). 
![variaveis](https://confluence.atlassian.com/confbr1/files/933709538/933709842/1/1489011355129/JAVA_HOME.png)
7. Clique em OK;
8. Crie uma nova variavel com o nome de **CLASS_PATH**
9. No campo **Valor da variável**, insira o seu caminho da instalação do JDK acrescentando **\lib;.** no final
   * Se preferir, pode utilizar a variavel **JAVA_HOME** criada anteriormente, basta inserir: **__%JAVA_HOME%\lib;.__** 

> Não esqueça de por **";."** no final, isso vai permitir que o sistema acesse todas as pastas dentro da pasta lib.

10. Clique em OK;
11. Agora procure pela variavel **Path** e clique para edita-la.
12. Clique no botão **Novo** e insira:
    * %JAVA_HOME%\bin
8. Clique em OK e Aplicar alterações quando solicitado.

>Você precisará fechar e abrir novamente qualquer janela de comando que estava aberta antes de fazer estas alterações, já que não há como recarregar variáveis de ambiente de um prompt de comando ativo. Se as alterações não entrarem em vigor depois de abrir novamente a janela de comando, reinicie o Windows.

#### Variaveis ANDROID SDK

1. Acesse as configurações de variaveis de ambiente do seu sistema. (Siga até o passo 3 da seção anterioror: **Variaveis JAVA**)
2. Sob **Variáveis do sistema**, clique em **Novo**
3. No campo **Nome da variável** insira:
   * ANDROID_HOME
4. No campo **Valor da variável**, insira o seu caminho da instalação do seu ANDROID SDK
>Se você não alterou o caminho durante a instalação, ele será parecido com isso **C:\Users\<Seu Usuario>\AppData\Local\Android\sdk**
5. Clique em OK;
6. Agora procure pela variavel **Path** e clique para edita-la.
7. Clique no botão **Novo** e insira:
   * %ANDROID_HOME%\emulator
   * %ANDROID_HOME%\platform-tools
   * %ANDROID_HOME%\tools
   * %ANDROID_HOME%\tools\bin
>A ordem é importante, obedeça o exemplo.
8. Clique em OK e Aplicar alterações quando solicitado.

#### Outras Variaveis

Também é interessante que você tenha algumas outras varivais no seu **Path** do sistema, para poder eventualmente utilizar recusos de linha de comando dos sistemas. Normalmente, essas variavis são configuradas automaticamente na hora da instalação do sistema, porém não custa nada conferir não é mesmo??

1. Agora, acesse o Painel de Controle do Windows, abra o item “Sistema”, clique em “Configurações avançadas do sistema”, selecione “Variáveis de ambiente”
2. Procure pela variavel **Path** e clique para edita-la.
3. Verifique se algum dos itens abaixo não consta entre as suas variaveis. Nesse caso, por favor as insira.

* __Git:__ C:\Program Files\Git\cmd
* __Node JS:__ C:\Program Files\nodejs\
* __Yarn:__ C:\Program Files (x86)\Yarn\bin\
* __Chocolatey__: C:\ProgramData\chocolatey\bin

### Instalando Dependencias

Abra o Propt de Comando do Windows e insira os seguintes comandos:

#### React Native

`> yarn global add react-native-cli`

>Caso não tenha instalado o Yarn, você pode usar: **npm install -g react-native-cli**

#### Aceitando Licensas do Emulador

`> sdkmanager --licenses`

Presione **Y** em todas as opções para aceitar as licensas.

### Testando

Para testar, Abra o Propt de Comando do Windows e siga as instruções:

#### Java 

`> java -version`
 
Se tudo der certo, você verá uma mensagem desse tipo: 

```
java version "1.8.0_202"
Java(TM) SE Runtime Environment (build 1.8.0_202-b08)
Java HotSpot(TM) 64-Bit Server VM (build 25.202-b08, mixed mode)
```
#### Node JS

`> node -v`

Se tudo der certo, você verá uma mensagem desse tipo:

```
v8.12.0
```
#### ADB

`> adb --version`
 
Se tudo der certo, você verá uma mensagem desse tipo: 

```
Android Debug Bridge version 1.0.41
Version 29.0.1-5644136
Installed as C:\Users\<Seu Usuario>\AppData\Local\Android\Sdk\platform-tools\adb.exe
```

#### Emulator

`> emulator -version`

Se tudo der certo, você verá uma mensagem desse tipo: 

```
Android emulator version 29.0.11.0 (build_id 5598178) (CL:N/A)
Copyright (C) 2006-2017 The Android Open Source Project and many others.
This program is a derivative of the QEMU CPU emulator (www.qemu.org).

  This software is licensed under the terms of the GNU General Public
  License version 2, as published by the Free Software Foundation, and
  may be copied, distributed, and modified under those terms.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.
```
#### React Native

`> react-native -v`

Se tudo der certo, você verá uma mensagem desse tipo: 

```
react-native-cli: 2.0.1
react-native: n/a - not inside a React Native project directory
```

````

## Contribuições

Aqui entraremos mais fundo no mundo do git. Para isso, é necessario que você tenha dominio basico dos comandos da ferramanta. Deixo aqui a sujestão de um [Guia Pratico](https://rogerdudler.github.io/git-guide/index.pt_BR.html) de Git para você não ter complicações.

Em nosso projeto, utilizamos adaptações da metodologia do git-flow. O git-flow é um conjunto de extensões para o git que provê operações de alto-nível para repositórios usando o modelo de branches do Vincent Driessen. [Saiba mais](https://nvie.com/posts/a-successful-git-branching-model/)

### Núcleo

No núcleo, o modelo de desenvolvimento é muito inspirado nos modelos existentes. 
O repositório central possui dois ramos principais com uma vida útil infinita:
   * **_master_**
      * Consideramos origin/master o ramo principal onde o código fonte HEAD sempre reflete um estado pronto para produção.
   * **_develop_**
      * Consideramos origin/develop o ramo principal em que o código-fonte HEAD sempre reflete um estado com as últimas alterações de desenvolvimento entregues para a próxima versão. Alguns chamariam isso de "ramo de integração". É aqui que todas as compilações noturnas automáticas são criadas.

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

### Criando Pull Requests


## Utilizando o Projeto

### Baixando o projeto

Para utilizar o projeto, você precisa ter configurado corretamente o seu ambeinte. Para fazer isso, acesse: [Configurando Ambeinte](https://pluggedcomputing.gitlab.io/post/environment_settings/).

1. Faça [download]() ou clone do repositorio.
   * Para clonar, abra o git bash na pasta onde deseja armazenar o projeto localmente e rode o comando: `> git clone "TODOOO"`
2. Abra o git bash na pasta baixada ou clonada;
3. Abra o projeto no Visual Studio Code ou na sua IDE de preferencia;
> Para abrir via linha de comando, execute o comando na pasta do projeto `> code .`.
4. Instale todas as dependencias usando o comando: `> yarn install` 
5. Aguarde o yarn instalar as dependencias e então seu projeto estará pronto para ser usado. 

### Iniciando Emulador

Para consultar os emuladores disponiveis na sua maquina, abra o Prompt de Comando do Windows e execute o seguinte comando:

`> emulator -list-avds`

Se tudo der certo, você verá uma mensagem desse tipo: 

```
Nexus_5X_API_28
Pixel_API_28
```
Agora, para iniciar o emulador, escolha uma das opções da lista e execute o comando:

`> emulator -avd Nexus_5X_API_28`
 Se você quiser da um boot "limpo" no seu emulador, pode usar:
 
`> emulator -no-snapshot -avd -avd Nexus_5X_API_28`

Se tudo der certo, o emulador será aberto na sua maquina.
 
> Se não existirem emuladores disponiveis, abra o Android Studio > AVD Manager e configure quantos emuladores quiser. 

## Boas Praticas

### Obrigatorias
1. Todos os nomes de variaveis, funções e metodos devem ser em ingles.
2. Deve ser aplicado o _design pattern [Model View Controller (MVC)](https://www.geeksforgeeks.org/mvc-design-pattern/)_.
4. Por padrão **não** usaremos **";"** no final dos comandos.
5. Deve-se utilizar um estilo de programação mais funcional, aproveitando-se dos metodos já existentes na lingaugem e das dependencias. **Nada de reinventar a roda...**
6. Todos os metodos devem ter um ou mais testes unitarios equivalentes. Usaremos o [Jest](https://jestjs.io/).

### Opcionais
1. Use o  [eslint](https://eslint.org/) ou [JS Lint](https://www.jslint.com/) para padronização do codigo fonte.
2. Sempre identar o codifo da maneira correta: `Ctrl + Alt + F`, no Visual Studio Code.
3. Utilizar comentarios nas funções e metodos e sempre que achar necessario.
4. Coloque os Scripts na Parte Final da Sua Página.
5. Declare Variáveis, Fora da Instrução For.
6. Use {} Ao Invés de New Object().
7. Use [] Ao Invés de New Array().
8. Use === Ao Invés de ==.
9. Crie estilos em arquivos separados.

## Referencias
* Configurando a variável JAVA_HOME no Windows. (2017). Disponivel em: <https://confluence.atlassian.com/confbr1/configurando-a-variavel-java_home-no-windows-933709538.html>
* Ambiente React Native. (2019). Diponivel em: <https://docs.rocketseat.dev/ambiente-react-native>
* Um modelo de ramificação Git bem-sucedido. (2010). Disponivel em: <https://nvie.com/posts/a-successful-git-branching-model/>