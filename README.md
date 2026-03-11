# FutApp (Canal Publico de Atualizacoes)

Repositorio publico usado pela app **KickOff** para distribuir atualizacoes OTA.

## Conteudo publicado

- `update/update.json`: manifesto com a versao atual, URL da APK e SHA-256.
- `dist/<versao>/kickoff.apk`: APK publica dessa versao.

## Versao atual

- Versao publicada: `3.4.9`
- APK: `dist/3.4.9/kickoff.apk`
- Manifesto: `https://raw.githubusercontent.com/Djmcarvalho/FutApp/main/update/update.json`
- APK publica: `https://raw.githubusercontent.com/Djmcarvalho/FutApp/main/dist/3.4.9/kickoff.apk`

## Processo de publicacao

1. Gerar a APK no repositorio principal.
2. Calcular o SHA-256 da APK final.
3. Copiar a APK para `dist/<versao>/kickoff.apk`.
4. Atualizar `update/update.json`.
5. Fazer commit e push no `main`.
6. Validar as URLs publicas.

## Regras

- Publicar apenas artefactos necessarios ao update.
- Nao incluir credenciais, tokens ou ficheiros internos.
- Manter o SHA-256 do manifesto alinhado com a APK publicada.
