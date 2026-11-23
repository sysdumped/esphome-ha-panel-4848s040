# Changelog

Formato basato su [Keep a Changelog](https://keepachangelog.com/it/1.1.0/),
versioni secondo [SemVer](https://semver.org/lang/it/) (in 0.x un aumento del minor può rompere la compatibilità).

## [Unreleased]

### Aggiunto
- CI: validazione della configurazione (`esphome config`) su ogni push e pull request,
  per la variante base e per quella con relè.
- Release automatica: un tag `vX.Y.Z` pubblica la release su GitHub con le note prese da questo file.

## [0.2.0] - 2026-11-23

### ⚠️ Breaking
- **Pagina Casa: la card termostato è sostituita da una terza card temperatura.**
  Nuove substitutions `ent_temp_3` / `label_temp_3`; `ent_climate` / `label_climate`
  rimosse (se restano nel deploy vengono ignorate).
- **`idle_timeout` e `brightness_idle` ora sono numeri senza unità.**
  Se nel tuo deploy li avevi impostati, aggiornali, altrimenti la build fallisce
  con `expected float`:
  - `idle_timeout: 60s` → `idle_timeout: "60"` (secondi)
  - `brightness_idle: "15%"` → `brightness_idle: "15"` (%)

### Aggiunto
- Due number regolabili da Home Assistant e mantenuti al riavvio:
  **Timeout dimming** (10–3600 s) e **Luminosità a riposo** (0–100 %).
  Le substitutions sopra ne impostano solo il valore iniziale.

### Rimosso
- Sensori del termostato e icona fiamma.

## [0.1.0] - 2026-11-11

Prima release testata su hardware reale.

### Aggiunto
- Pannello LVGL per Guition ESP32-S3-4848S040: pagina **Casa** (consumi su arco con soglie,
  temperature interna/esterna, termostato, 3 tasti luce) e pagina **Stanze** (4 temperature).
- Dimming automatico dopo inattività, disattivabile con lo switch **Dimming automatico**.
- `log_level` / `lvgl_log_level` per il debug del touch.
- Package opzionale per il modulo 3 relè.

### Corretto
- Mappatura del touch GT911 con `calibration` esplicita (il controller dichiara 1024×600
  ma invia coordinate 0..480).
- Rotazione spostata nella configurazione LVGL; testo a basso contrasto.

[Unreleased]: https://github.com/sysdumped/esphome-ha-panel-4848s040/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/sysdumped/esphome-ha-panel-4848s040/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/sysdumped/esphome-ha-panel-4848s040/releases/tag/v0.1.0
