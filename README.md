# app-model

Aplicativo React Native com Expo.

## Visão geral

Este projeto usa Expo para desenvolvimento e EAS Build para geração de builds para publicação em lojas.

## Requisitos

- Node.js 18+  
- npm  
- Git  
- `expo-cli` e `eas-cli`  
- Android Studio para testes Android locais  
- macOS + Xcode para builds iOS locais (opcional se usar EAS na nuvem)  
- Conta Expo (recomendada)  
- Conta Google Play Developer (US$25 taxa única)  
- Conta Apple Developer Program (US$99/ano)

## Instalação

No terminal na raiz do projeto:

```
npm install
```

Instale CLI globalmente ou use `npx`:

```
npm install -g expo-cli eas-cli
```

## Configuração do projeto

### app.json

Certifique-se de ter `app.json` com as informações do app:

```json
{
  "expo": {
    "name": "app-model",
    "slug": "app-model",
    "version": "1.0.0",
    "platforms": ["ios", "android", "web"],
    "ios": {
      "bundleIdentifier": "com.seunome.appmodel"
    },
    "android": {
      "package": "com.seunome.appmodel"
    }
  }
}
```

### eas.json

Crie ou ajuste `eas.json`:

```json
{
  "cli": {
    "version": ">= 3.0.0"
  },
  "build": {
    "production": {
      "android": {
        "buildType": "app-bundle"
      },
      "ios": {
        "simulator": false
      }
    }
  }
}
```

## Comandos principais

### Rodar localmente

```
npm start
```

Ou:

```
expo start
```

### Android em desenvolvimento

```
expo run:android
```

### Web

```
npm run web
```

### Gerar bundle de produção

```
npx expo export --output-dir ./dist
```

## Gerar builds para publicação

### Android (AAB)

```
npx eas build -p android --profile production
```

Para gerar APK, ajuste `eas.json`:

```json
"android": {
  "buildType": "apk"
}
```

### iOS (IPA)

```
npx eas build -p ios --profile production
```

> Em Windows só é possível gerar IPA usando EAS Build na nuvem.

## Publicação

### Google Play Store

1. Criar Google Play Developer account
2. Pagar taxa única de US$25
3. Criar app no Play Console
4. Enviar `app.aab`
5. Preencher descrições, imagens, políticas e classificação de conteúdo
6. Submeter para revisão

### Apple App Store

1. Criar Apple ID
2. Inscrever-se no Apple Developer Program
3. Pagar US$99/ano
4. Ativar autenticação de dois fatores
5. Criar app no App Store Connect
6. Enviar `ipa` gerado pelo EAS
7. Preencher metadados, capturas e políticas
8. Submeter para revisão

## Notas

- Não use `npx react-native run-android` em projetos Expo padrão.
- Use `expo start` para desenvolvimento local.
- Adicione `node_modules/`, `.expo/`, `.expo-shared/` e outros arquivos locais em `.gitignore`.
- Verifique os identificadores `bundleIdentifier` e `android.package` antes da publicação.