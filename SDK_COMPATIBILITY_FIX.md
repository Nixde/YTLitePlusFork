# SDK 26.0 Compatibility Fix

## Problema

Il workflow di GitHub Actions falliva con errori di compilazione come:

```
module '_c_standard_library_obsolete' requires feature 'found_incompatible_headers__check_search_paths'
fatal error: could not build module '_Builtin_float'
fatal error: could not build module 'CoreFoundation'
```

## Causa

- L'SDK iOS 26.0 (incluso in Xcode 16.5+) introduce breaking changes nei moduli della libreria C standard
- Questi cambiamenti richiedono la feature `found_incompatible_headers__check_search_paths`
- Le toolchain di Theos e le dipendenze (Alderis, libcolorpicker, ecc.) non supportano ancora questa feature
- Il runner `macos-15-intel` include Xcode 16.5+ con SDK 26.0 che causava il conflitto

## Soluzione Implementata

### 1. Cambio Runner
- **Prima**: `runs-on: macos-15-intel` (Xcode 16.5+ con SDK 26.0)
- **Dopo**: `runs-on: macos-14` (Xcode 16.1 o precedente, senza SDK 26.0)

### 2. Forzatura SDK Esplicita
Aggiunto nuovo step "Force SDK Selection and Prevent System SDK Conflicts" che:
- Imposta `SDKROOT` esplicitamente alla versione SDK scaricata (default 17.5)
- Previene l'uso automatico dell'SDK di sistema incompatibile
- Verifica che il percorso SDK sia corretto prima della compilazione

### 3. Build con SDK Esplicito
Modificato il comando make per passare `SDKROOT` esplicitamente:
```bash
make package SIDELOAD=1 THEOS_PACKAGE_SCHEME=rootless FINALPACKAGE=1 SDKROOT="$SDKROOT"
```

## Modifiche ai File

### `.github/workflows/buildapp.yml`
1. Linea 57: Cambiato `runs-on: macos-15-intel` → `runs-on: macos-14`
2. Linee 117-127: Aggiunto step per forzare selezione SDK
3. Linee 181-186: Aggiunta verifica SDK e passaggio esplicito a make

## Note per il Futuro

Quando Theos e le sue dipendenze saranno aggiornate per supportare SDK 26.0:
1. Si potrà tornare a usare `macos-15-intel` o runner più recenti
2. Lo step "Force SDK Selection" potrà essere rimosso o semplificato
3. Sarà possibile aggiornare il default SDK version da 17.5 a versioni più recenti

## Riferimenti

- [Swift Forums: SDK 26.0 breaking changes](https://forums.swift.org/t/xcode-16-5-beta-sdk-issues/...)
- [GitHub Issue: Rust project with same problem](https://github.com/.../issues/...)
- Soluzione comune nella community: downgrade a SDK precedente fino al supporto ufficiale
