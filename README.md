## cls

* add the following line to .bashrc:
```
alias cls='tput reset'
```

## Thunderbird Lightning

```
sudo apt install lightning
sudo apt install lightning-l10n-de
```

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

## TypeScript via Node.js

```
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt install -y nodejs

npm config set prefix '~/.npm-global'
npm install -g typescript
```
* add the following line to .bashrc:
```
export PATH=~/.npm-global/bin:$PATH
```
* close the shell


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
