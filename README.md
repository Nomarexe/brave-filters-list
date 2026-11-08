# SiteBlock

## Liste

- [NoPorno](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/SiiteBlock/NoPorno.txt)
- [NoGames](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/SiiteBlock/NoGames.txt)
- [NoFakeNews](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/SiiteBlock/NoFakeNews.txt)

## Installazione e aggiornamento

Lo script scarica le liste nella cartella da cui viene eseguito.

```bash
#!/usr/bin/env bash

DEST="$PWD"
errori=0

while IFS='|' read -r nome url; do
    file="$DEST/$nome"
    tmp="$(mktemp "$DEST/.download.XXXXXX")" || {
        echo "ERRORE: impossibile creare un file temporaneo per $nome" >&2
        errori=1
        continue
    }

    if curl -fLsS --retry 3 --connect-timeout 20 --max-time 180 --compressed \
        -o "$tmp" "$url" && [[ -s "$tmp" ]] && mv -f -- "$tmp" "$file"; then
        echo "OK: $nome"
    else
        rm -f -- "$tmp"
        echo "ERRORE: $nome" >&2
        errori=1
    fi
done <<'LISTE'
NoPorno.txt|https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/SiiteBlock/NoPorno.txt
NoGames.txt|https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/SiiteBlock/NoGames.txt
NoFakeNews.txt|https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/SiiteBlock/NoFakeNews.txt
LISTE

echo "File scaricati/aggiornati in: $DEST"
exit "$errori"
```

# Clean

## Liste

- [CleanFacebook](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Focus/CleanFacebook.txt)
- [CleanYoutube](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Focus/CleanYoutube.txt)

## Installazione e aggiornamento

Lo script scarica le liste nella cartella da cui viene eseguito.

```bash
#!/usr/bin/env bash

DEST="$PWD"
errori=0

while IFS='|' read -r nome url; do
    file="$DEST/$nome"
    tmp="$(mktemp "$DEST/.download.XXXXXX")" || {
        echo "ERRORE: impossibile creare un file temporaneo per $nome" >&2
        errori=1
        continue
    }

    if curl -fLsS --retry 3 --connect-timeout 20 --max-time 180 --compressed \
        -o "$tmp" "$url" && [[ -s "$tmp" ]] && mv -f -- "$tmp" "$file"; then
        echo "OK: $nome"
    else
        rm -f -- "$tmp"
        echo "ERRORE: $nome" >&2
        errori=1
    fi
done <<'LISTE'
CleanFacebook.txt|https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Focus/CleanFacebook.txt
CleanYoutube.txt|https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Focus/CleanYoutube.txt
LISTE

echo "File scaricati/aggiornati in: $DEST"
exit "$errori"
```

# Plus

## Liste

- [AdGuard Tracking Protection](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Plus/adguard-tracking-protection.txt)
- [Hagezi Native Amazon](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Plus/hagezi-native-amazon.txt)
- [Hagezi Native Apple](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Plus/hagezi-native-apple.txt)
- [Hagezi Native Microsoft](https://raw.githubusercontent.com/Nomarexe/brave-filters-list/refs/heads/main/Plus/hagezi-native-microsoft.txt)

Per installare e aggiornare queste liste, usa lo script della sezione **Plus sources**.
