# KickOff

Aplicação Android para consulta de competições da FPF, orientada por clube ativado por código.

## Estado Atual

- Nome comercial: `KickOff`
- Versão atual no projeto: `3.5.39`
- APK gerada: `kickoff.apk`
- Atualização OTA: GitHub público `Djmcarvalho/FutApp` no branch `main`
- Base local: Room/SQLite com sincronização em background
- Arquitetura: MVVM com coordenadores e serviços dedicados

## Funcionalidades Principais

- Ativação por código numérico de 5 dígitos
- Associação da app a um único clube após ativação
- Alteração de código através de hotspot invisível no canto superior direito
- Carregamento inicial a partir da base de dados local
- Consulta em background à FPF sem bloquear a interface
- Sincronização silenciosa com persistência local automática
- Consulta de épocas disponíveis
- Consulta de competições válidas para o clube ativado
- Jogos e classificação organizados por competição e fase
- Atualização manual por gesto de deslizar para baixo
- Verificação de atualização da app no menu `Info`
- Splash em vídeo antes da abertura da app

## Estrutura Principal

### Interface e Estado

- [MainActivity.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/MainActivity.kt)
- [MainViewModel.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/MainViewModel.kt)
- [MainUiState.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/MainUiState.kt)

### Sincronização e Domínio

- [FpfCalendarService.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/FpfCalendarService.kt)
- [FpfFixtureParser.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/FpfFixtureParser.kt)
- [FpfHttpCacheGateway.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/FpfHttpCacheGateway.kt)
- [CalendarSyncCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/CalendarSyncCoordinator.kt)

### Persistência Local

- [CalendarSnapshotRepository.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/CalendarSnapshotRepository.kt)
- [AppDatabase.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/AppDatabase.kt)

### Ativação e Atualização

- [ActivationCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/ActivationCoordinator.kt)
- [ActivationDialogCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/ActivationDialogCoordinator.kt)
- [AppUpdateCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/AppUpdateCoordinator.kt)
- [AppUpdateUiCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/AppUpdateUiCoordinator.kt)
- [ApkInstallCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/ApkInstallCoordinator.kt)

## Build e Testes

```powershell
./android/gradlew.bat -p android build
./android/gradlew.bat -p android testDebugUnitTest
```

Em Windows, quando existir ruído de cache do Kotlin/Gradle:

```powershell
./android/gradlew.bat -p android --no-daemon -Dkotlin.incremental=false -Dkotlin.compiler.execution.strategy=in-process assembleDebug
```

## Deploy para GitHub

O deploy OTA é publicado no repositório público [`Djmcarvalho/FutApp`](https://github.com/Djmcarvalho/FutApp) no branch `main`.

- Ele compila o APK debug.
- Copia o binario para `dist/<versao>/kickoff.apk`.
- Regera `update/update.json` com SHA-256 valido.
- Faz commit e push desses ficheiros para o branch `main` do repositório público.

## Compatibilidade

- `applicationId`: `pt.vieirasc.appfut`
- A app usa `kickoff_local_cache.db`, com migração automática a partir da base antiga

## Estado do Plano Técnico

- Fase 1: concluída
- Fase 2: concluída
- Fase 3: concluída
- Fase 4: concluída
- Fase 6: estabilização e refinamento final
