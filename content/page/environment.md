---
title: Configuração de Ambiente
subtitle: Why you'd want to hang out with me
comments: false
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
12. Clique no botão **Novo** e insira:
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
