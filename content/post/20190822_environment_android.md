---
title: Variaveis ANDROID SDK
date: 2019-08-22
---
Os exemplos utilizados aqui serão baseados no **Windows 10**.   Caso seu sistema operacional seja Linux ou macOS, você pode consultar os seguintes tutoriais: [Linux](https://docs.rocketseat.dev/ambiente-react-native/android/linux#configurando-sdk-do-android-no-linux) | [macOS](https://docs.rocketseat.dev/ambiente-react-native/android/macos#configurando-sdk-do-android-no-macos)

1. Localize o diretório de instalação Java
>Se você não alterou o caminho durante a instalação, ele será parecido com isso **__C:\Program Files\Java\jdk1.8.0_65__**
2. Vá para **Painel de controle** > **Sistema** > **Configurações avançadas do sistema**
3. Clique no botão **Variáveis de ambiente**
4. Sob **Variáveis do sistema**, clique em **Novo**
   * ANDROID_HOME
5. No campo **Valor da variável**, insira o seu caminho da instalação do seu ANDROID SDK
>Se você não alterou o caminho durante a instalação, ele será parecido com isso **C:\Users\<Seu Usuario>\AppData\Local\Android\sdk**
6. Clique em OK;
7. Agora procure pela variavel **Path** e clique para edita-la.
8. Clique no botão **Novo** e insira:
   * %ANDROID_HOME%\emulator
   * %ANDROID_HOME%\platform-tools
   * %ANDROID_HOME%\tools
   * %ANDROID_HOME%\tools\bin
>A ordem é importante, obedeça o exemplo.
9. Clique em OK e Aplicar alterações quando solicitado.

>Você precisará fechar e abrir novamente qualquer janela de comando que estava aberta antes de fazer estas alterações, já que não há como recarregar variáveis de ambiente de um prompt de comando ativo. Se as alterações não entrarem em vigor depois de abrir novamente a janela de comando, reinicie o Windows.