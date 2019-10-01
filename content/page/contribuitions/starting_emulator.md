---
title: Iniciando o Emulador
subtitle: Guia de como iniciar o emulador para executar seu projeto react native
comments: false
date: 2019-08-27
---

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