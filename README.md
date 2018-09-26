## cls

* add the following line to .bashrc:
```
alias cls='tput reset'
```

## TypeScript via Node.js

```
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt install -y nodejs
```

* add the following line to ~/.profile:
```
export PATH=~/.npm-global/bin:$PATH
```

```
source ~/.profile
npm config set prefix '~/.npm-global'
npm install -g typescript
```

## ipe

```
sudo apt install ipe
sudo apt install texlive-latex-extra

iperender -svg input.xml output.svg
```

## LibreOffice Writer

```
Extras / Optionen... / LibreOffice Writer / Kompatibilität
[ ] Absatz- und Tabellenabstände AN SEITENANFÄNGEN addieren (aktuelles Dokument)
```

## Merge video segments

```
ffmpeg -f concat -i inputs.txt -c copy output.mp4
```
* inputs.txt
```
file a.mp4
file b.mp4
file c.mp4
```

## Bootable Windows installer

* format USB stick with fat32
* set boot flag (via gparted)
* copy files inside ISO file onto USB stick
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
