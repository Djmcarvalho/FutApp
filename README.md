# FutApp (Canal Público de Atualizações)

Este repositório é o canal público de distribuição da aplicação **KickOff**.

## Objetivo

Servir ficheiros públicos para o sistema de atualização automática da app Android:

- `update/update.json` (manifesto de atualização)
- `dist/<versao>/kickoff.apk` (APK da versão)

## Estrutura

- `update/update.json`
- `dist/3.4.8/kickoff.apk`
- `dist/3.4.7/kickoff.apk`
- `dist/2.0/kickoff.apk`
- `dist/2.1/kickoff.apk`
- `dist/2.2/kickoff.apk`
- `dist/3.4.7/kickoff.apk`
- `dist/3.4.7/kickoff.apk`
- `dist/3.4.7/kickoff.apk`
- `dist/3.4.7/kickoff.apk`

## Versão Atual

- Versão publicada: `3.4.8`
- APK: `dist/3.4.8/kickoff.apk`

## URLs Públicas

- Manifesto:
  - `https://raw.githubusercontent.com/Djmcarvalho/FutApp/main/update/update.json`
- APK 3.4.8:
  - `https://raw.githubusercontent.com/Djmcarvalho/FutApp/main/dist/3.4.8/kickoff.apk`

## Processo de Publicação

1. Gerar a APK no repositório privado de desenvolvimento.
2. Calcular SHA-256 da APK final.
3. Copiar APK para `dist/<versao>/kickoff.apk` neste repositório.
4. Atualizar `update/update.json` com:
   - `versionCode`
   - `versionName`
   - `apkUrl`
   - `apkSha256`
   - `releaseNotes`
   - `changelog`
5. Fazer commit e push no `main`.
6. Validar as URLs públicas (`HTTP 200`).

## Segurança

- Este repositório deve conter apenas artefactos públicos de atualização.
- Não incluir tokens, credenciais, ficheiros internos ou dados sensíveis.
- O SHA-256 no manifesto deve corresponder exatamente ao APK publicado.

## Nota

O código-fonte principal da aplicação pode permanecer privado. A app consome apenas este repositório público para updates.


