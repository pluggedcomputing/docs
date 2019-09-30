---
title: Variaveis  JAVA
subtitle: Guia de configuração completo para variaveis JAVA
comments: false
date: 2019-08-21
---
Os exemplos utilizados aqui serão baseados no **Windows 10**.   Caso seu sistema operacional seja Linux ou macOS, você pode consultar os seguintes tutoriais: [Linux](https://docs.rocketseat.dev/ambiente-react-native/android/linux#configurando-sdk-do-android-no-linux) | [macOS](https://docs.rocketseat.dev/ambiente-react-native/android/macos#configurando-sdk-do-android-no-macos)

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