---
title: Migrar Expo para ReactNative CLI
date: 2020-07-03
---

## 1: Configuração de ambiente e instalação do ReactNative CLI, seguindo os passos em https://reactnative.dev/docs/0.60/getting-started

## 2: Criar novo projeto ReactNative CLI com o comando `npx react-native init nome_projeto`

## 3: Copiar os arquivos `src`, `App.js` e para o arquivo `package.json` siga as instruções:

- Copie as dependências `dependencies` e `devDependencies` do arquivo `package.json` do projeto em expo para o projeto em cli.

* Remova `"react-native": "https://github.com/expo/react-native/archive/sdk-36.0.0.tar.gz"` e deixe apenas `"react-native": "0.62.2"`

## 4: Execute o comando npm install para baixar as dependências

## 5: Copiar o arquivo `commitlint.config.js` do projeto anterior para o novo projeto.

## 6: No arquivo `package.json` faça as seguintes alterações, depois execute o comando `npm install`:

- substiuição

  - "expo-linear-gradient": "~8.0.0" -> "react-native-linear-gradient": "^2.5.6"

  - "lottie-react-native": "~2.6.1" -> "lottie-ios": "3.1.3",
    "lottie-react-native": "^3.4.0"

- remoção

  - "@expo/vector-icons": "^10.0.6"

  - "expo": "~36.0.0"

  - "expo-constants": "~8.0.0"

  - "expo-font": "~8.0.0"

  - "babel-preset-expo": "~8.0.0",

* adicionar

  - "@react-native-community/async-storage": "^1.11.0"

## 7: No arquivo `App.js` copie e cole o codigo abaixo:

    import React from 'react';

    import {setCustomTextInput, setCustomText} from 'react-native-global-props';

    import Routes from './src/routes';
    import {general} from './src/styles';

    const customTextInputProps = {
    style: general.customProps,
    };

    const customTextProps = {
    style: general.customProps,
    };

    setCustomTextInput(customTextInputProps);
    setCustomText(customTextProps);

    const App = () => {
    return <Routes />;
    };

    export default App;

## 8: No `index.js` dos componentes `LoginOrRegister` e `ScreenAbout` faça:

- import {LinearGradient} from 'expo-linear-gradient' -> import LinearGradient from 'react-native-linear-gradient'

## 9: No `index.js` dos componentes `Congratulations` e `LevelSelection` faça:

- import {..., AsyncStorage, ...} -> import AsyncStorage from '@react-native-community/async-storage'

## 10: No `index.js` do componete `Exercises` faça:

- impot {MaterialCommunityIcons} from '@expo/vector-icons' -> import Icon from 'react-native-vector-icons/MaterialCommunityIcons'

* Modifique

  ```
  <MaterialCommunityIcons name="lightbulb-on-outline"
  size={general.iconSize.bigger}
  style={styles.icon}
  onPress={handleTips}
  ```

  Para

  ```
  <Icon .. name="lightbulb-on-outline"
  size={general.iconSize.bigger}
  style={styles.icon}
  onPress={handleTips}./>
  ```

- No terminal execute o comando `yarn add react-native-vector-icons`

## 11: Instalar dependência babel present-env com o comando `npm install --save-dev @babel/preset-env`

## 12: Adicionar configuração para Fonts faça:

- No terminal na raiz do projeto execute `echo "module.exports = {assets: ['./assets/fonts/Poppins'],};" > react-native.config.js`

- Na raiz do projeto crie as pastas `assets/fonts/Poppins/` depois copie e cole o conteudo da pasta `src/assets/fonts` dentro.

* Execute o seguinte codigo no terminal `react-native link`

## 13: Mudar versão minima do android, na pasta `android` no arquivo `build.gragle` mude minSdkVersion para 19

## 14: Para o ReactNative funcionar na versão 19 do android, faça os seguintes paços:

1. Abra o Android Studio va em `File` -> `open` -> `va até a pasta do prejeto` e depois selecione a pasta `android`

1. Em `Gradle Scripts` abra o arquivo `build.gragle(Module:app)`

1. Em `dependêncies` adicione o codigo a baixo, depois aperte em Sync Now

```
 implementation ("com.squareup.okhttp3:okhttp:3.12.12"){
      force = true //API 19 support
  }
  implementation 'com.squareup.okhttp3:logging-interceptor:3.12.12'
```

## 15: Rodar o projeto com o comando `npx react-native run-android`

## 16: Caso ocorra o erro da imagem a baixo, execute o comando `npx react-native start`

![Image erro run android](https://user-images.githubusercontent.com/5674956/59913382-ab528400-9435-11e9-9215-77fcbd5b9b98.jpeg)
