## cls

* add the following line to .bashrc:
```
alias cls='tput reset'
```

## Cinnamon

```
sudo sed -i "s|mini=20, maxi=60,|mini=40, maxi=120,|g" /usr/share/cinnamon/cinnamon-settings/modules/cs_panel.py
```

## Firefox

* enter `about:config` as URL
* accept the risk
* set `layers.acceleration.force-enabled` to `true` via double-click
* restart Firefox

## LibreOffice Writer

```
Extras / Optionen... / LibreOffice Writer / Kompatibilität
[ ] Absatz- und Tabellenabstände AN SEITENANFÄNGEN addieren (aktuelles Dokument)
```

## ipe

```
sudo apt install ipe
sudo apt install texlive-latex-extra

./xml2svg
```

## Markdown PDF

* https://www.google.com/chrome
  * download .deb file
  * install .deb file via double-click
* https://code.visualstudio.com/download
  * download .deb file
  * install .deb file via double-click
  * launch from start menu or via `code`
* Ctrl+Shift+P `settings`
  * Preferences: Open Settings (JSON)
  * insert `"markdown-pdf.executablePath": "/usr/bin/google-chrome",`
  * Ctrl+S
* Ctrl+Shift+X
  * Search Extensions in Marketplace: `markdown pdf`
  * Markdown PDF **yzane** `Install`
* right-click inside .md file
  * Markdown PDF: Export (pdf)

## Node.js and TypeScript

```
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt install -y nodejs

npm config set prefix '~/.npm-global'
npm install -g typescript
```
* add the following line to .bashrc:
```
export PATH=~/.npm-global/bin:$PATH
```
* close the terminal

### Local development with ES6 modules

* Browsers reject loading modules from the file system with a CORS error
* Hence the project files must be served by a local web server:

```
npm install -g http-server

cd project
http-server
firefox localhost:8080
```

## Bootable Windows installer

* format USB stick with NTFS
* set boot flag (via gparted)
* copy files inside ISO file onto USB stick
  * closing the target window may increase throughput significantly on NTFS
```
sudo grub-install --boot-directory=/media/USER-NAME/STICK-NAME /dev/sdX
```
* create grub/grub.cfg with the following content:
```
menuentry 'Install Windows' {
 ntldr /bootmgr
}
```

## Fix Windows master boot record

```
bootsect /nt60 c: /mbr
```

## Remove github Windows credentials

* Anmeldeinformationsverwaltung
* Windows-Anmeldeinformationen
* git:https://github.com aufklappen
* Entfernen
