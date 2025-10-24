# "voltronic_addon" je Addon do HA.

### Zdroj:
    - https://github.com/lavron/docker-voltronic-mqtt
    - Supports protocols PI30 and PI41 devices.

### Poznámka:
    - V "config.yaml" je potřeba nastavit správnou cestu k Docker obrazu. Koncovka označuje architekturu procesoru, na kterém je Docker runtime spuštěn.
    - Nastavit cestu k sériovému portu.
    - "config.yaml" a "run.sh" by měly mít oddělovače řádků LF
