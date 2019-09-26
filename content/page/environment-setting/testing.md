---
title: Testando
date: 2019-09-27
---

Para testar, Abra o Propt de Comando do Windows e siga as instruções:

#### Java 
 ```cmd
 > java -version
 ````
 
 Se tudo der certo, você verá uma mensagem desse tipo: 
 ```cmd
java version "1.8.0_202"
Java(TM) SE Runtime Environment (build 1.8.0_202-b08)
Java HotSpot(TM) 64-Bit Server VM (build 25.202-b08, mixed mode)
````

#### Node JS
 ```cmd
 > node -v
 ````

 Se tudo der certo, você verá uma mensagem desse tipo: 
 ```cmd
v8.12.0
````

#### ADB
 ```cmd
 > adb --version
 ````
 Se tudo der certo, você verá uma mensagem desse tipo: 
 ```cmd
Android Debug Bridge version 1.0.41
Version 29.0.1-5644136
Installed as C:\Users\<Seu Usuario>\AppData\Local\Android\Sdk\platform-tools\adb.exe
````

#### Emulator
 ```cmd
 > emulator -v
 ````
 Se tudo der certo, você verá uma mensagem desse tipo: 
 ```cmd
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
````
#### React Native
 ```cmd
 > react-native -v
 ````
 Se tudo der certo, você verá uma mensagem desse tipo: 
 ```cmd
react-native-cli: 2.0.1
react-native: n/a - not inside a React Native project directory
````

## Iniciando Emulador
Para consultar os emuladores disponiveis na sua maquina, abra o Prompt de Comando do Windows e execute o seguinte comando:
 ```cmd
 > emulator -list-avds
 ````
 Se tudo der certo, você verá uma mensagem desse tipo: 
 ```cmd
Nexus_5X_API_28
Pixel_API_28
````
Agora, para iniciar o emulador, escolha uma das opções da lista e execute o comando:

 ```cmd
 > emulator -avd Nexus_5X_API_28
 ````
 Se tudo der certo, o emulador será aberto na sua maquina.
 >Se não existirem emuladores disponiveis, abra o Android Studio > AVD Manager e configure quantos emuladores quiser. 