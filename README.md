## cls

* add the following line to .bashrc:
```
alias cls='tput reset'
```

## Firefox

* enter `about:config` as URL
* accept the risk
* set `layers.acceleration.force-enabled` to `true` via double-click
* restart Firefox

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

## Markdown PDF

* `sudo apt install chromium`
  * `which chromium` should print `/usr/bin/chromium`
* https://code.visualstudio.com/download
  * download .deb file
  * install .deb file via double-click
  * launch from start menu or via `code`
* Ctrl+Shift+P `settings`
  * Preferences: Open Settings (JSON)
  * insert `"markdown-pdf.executablePath": "/usr/bin/chromium"`
  * Ctrl+S
* Ctrl+Shift+X
  * Search Extensions in Marketplace: `markdown pdf`
  * Markdown PDF **yzane** `Install`
* right-click inside .md file
  * Markdown PDF: Export (pdf)

## Pseudo-stereo videos

* duplicate left channel:
```
ffmpeg -i input.mp4 -map_channel 0.1.0 -map_channel 0.1.0 -c:v copy stereo.mp4
```

* duplicate right channel:
```
ffmpeg -i input.mp4 -map_channel 0.1.1 -map_channel 0.1.1 -c:v copy stereo.mp4
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

## Windows Subsystem for Linux

* open PowerShell **as Administrator** and enable WSL:
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
* confirm computer restart
* download https://aka.ms/wsl-debian-gnulinux
* double-click on .appx file and select Install
* pick username and password
```
sudo apt update
```

### git

```
sudo apt install git
git --version
git config --global core.autocrlf true
```

### Maven

```
sudo apt install openjdk-8-source
javac -version
sudo apt install maven
mvn --version
```
* to share the local repository, create ~/.m2/settings.xml with the following content:
```
<settings>
    <localRepository>/mnt/c/Users/fred/.m2/repository</localRepository>
</settings>
```

> Error: Could not find or load main class org.apache.maven.surefire.booter.ForkedBooter

* add the following line to .bashrc until [the issue](https://stackoverflow.com/questions/53010200) is resolved:
```
export _JAVA_OPTIONS=-Djdk.net.URLClassPath.disableClassPathURLCheck=true
```
