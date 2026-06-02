# KickOff

AplicaÃ§Ã£o Android para consulta de competiÃ§Ãµes da FPF, orientada por clube ativado por cÃ³digo.

## Estado Atual

- Nome comercial: `KickOff`
- VersÃ£o atual no projeto: `3.5.40`
- APK gerada: `kickoff.apk`
- AtualizaÃ§Ã£o OTA: GitHub pÃºblico `Djmcarvalho/FutApp` no branch `main`
- Base local: Room/SQLite com sincronizaÃ§Ã£o em background
- Arquitetura: MVVM com coordenadores e serviÃ§os dedicados

## Funcionalidades Principais

- AtivaÃ§Ã£o por cÃ³digo numÃ©rico de 5 dÃ­gitos
- AssociaÃ§Ã£o da app a um Ãºnico clube apÃ³s ativaÃ§Ã£o
- AlteraÃ§Ã£o de cÃ³digo atravÃ©s de hotspot invisÃ­vel no canto superior direito
- Carregamento inicial a partir da base de dados local
- Consulta em background Ã  FPF sem bloquear a interface
- SincronizaÃ§Ã£o silenciosa com persistÃªncia local automÃ¡tica
- Consulta de Ã©pocas disponÃ­veis
- Consulta de competiÃ§Ãµes vÃ¡lidas para o clube ativado
- Jogos e classificaÃ§Ã£o organizados por competiÃ§Ã£o e fase
- AtualizaÃ§Ã£o manual por gesto de deslizar para baixo
- VerificaÃ§Ã£o de atualizaÃ§Ã£o da app no menu `Info`
- Splash em vÃ­deo antes da abertura da app

## Estrutura Principal

### Interface e Estado

- [MainActivity.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/MainActivity.kt)
- [MainViewModel.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/MainViewModel.kt)
- [MainUiState.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/MainUiState.kt)

### SincronizaÃ§Ã£o e DomÃ­nio

- [FpfCalendarService.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/FpfCalendarService.kt)
- [FpfFixtureParser.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/FpfFixtureParser.kt)
- [FpfHttpCacheGateway.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/FpfHttpCacheGateway.kt)
- [CalendarSyncCoordinator.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/CalendarSyncCoordinator.kt)

### PersistÃªncia Local

- [CalendarSnapshotRepository.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/CalendarSnapshotRepository.kt)
- [AppDatabase.kt](C:/Users/duarte.carvalho/Documents/VsCode%20Projects/App%20Fut/android/app/src/main/kotlin/pt/vieirasc/appfut/AppDatabase.kt)

### AtivaÃ§Ã£o e AtualizaÃ§Ã£o

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

Em Windows, quando existir ruÃ­do de cache do Kotlin/Gradle:

```powershell
./android/gradlew.bat -p android --no-daemon -Dkotlin.incremental=false -Dkotlin.compiler.execution.strategy=in-process assembleDebug
```

## Deploy para GitHub

O deploy OTA Ã© publicado no repositÃ³rio pÃºblico [`Djmcarvalho/FutApp`](https://github.com/Djmcarvalho/FutApp) no branch `main`.

- Ele compila o APK debug.
- Copia o binario para `dist/<versao>/kickoff.apk`.
- Regera `update/update.json` com SHA-256 valido.
- Faz commit e push desses ficheiros para o branch `main` do repositÃ³rio pÃºblico.

## Compatibilidade

- `applicationId`: `pt.vieirasc.appfut`
- A app usa `kickoff_local_cache.db`, com migraÃ§Ã£o automÃ¡tica a partir da base antiga

## Estado do Plano TÃ©cnico

- Fase 1: concluÃ­da
- Fase 2: concluÃ­da
- Fase 3: concluÃ­da
- Fase 4: concluÃ­da
- Fase 6: estabilizaÃ§Ã£o e refinamento final
