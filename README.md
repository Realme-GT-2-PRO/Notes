# Notes

>  Made By : [Omkar Parte](https://t.me/rakmoparte) ( RAKMOSOLUTIONS )

# GMS UPDATE GUIDE

## Apk disassembler

- Repo https://github.com/cryptax/droidlysis
```
pip install droidlysis
```

- After Setup
```
droidlysis --input SetupWizardPixelPrebuilt.apk .apk --output DIR --config /home/ram-unlok/softs/venv/lib/python3.10/site-packages/conf/general.conf
```

## Update Strings

- Only add strings to stagging
```
git add '*strings.xml
```

- Replace Pixel with ROM Name
```
grep -rli 'Pixel' | xargs sed -i 's/Pixel/EverestOS/g'
```
```
grep -rli ' your' | xargs sed -i 's/ your//g'
```

### This Repo Contains All Kinds Of Configs, Notes, Bringup, Changelogs, Etc.
