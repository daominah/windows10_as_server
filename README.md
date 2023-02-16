# Setup a personal computer as a Windows server

## Steps

### 1. Create boot USB

* Download [Microsoft Windows 10 installation media creation tool](https://www.microsoft.com/en-us/software-download/windows10%20)
* [daominah's mirror](https://drive.google.com/file/d/1EifPAsUygky0VwuFMhM1L8vW6MOHJU4_/view?usp=share_link)

### 2. Install and update Windows

After installed, set a meaningful computer name, example `tungdtWindowsGram17z90q`.

### 3. Pirate

* Full guide: [github.com/massgravel/Microsoft-Activation](https://github.com/massgravel/Microsoft-Activation-Scripts)
* Brief: `Windows PowerShell` as admin:
  ````
  irm https://massgrave.dev/get | iex
  ````

### 4. Enable administrator account

* Full guide: [groovypost.com/howto/enable-admin](https://www.groovypost.com/howto/enable-disable-built-in-administrator-account-windows-10/)

  Brief: `cmd.exe` as admin:
  ````
  net user administrator /active:yes
  ````

* Disable default `Quick Edit` in `cmd`.

* Set administrator account password (default admin does not have a password):

  * `Sign-in options`: `Password`: `Add`

### 5. Remote control

#### 5.1. TeamViewer

* Download the [installer](https://www.teamviewer.com/en/download/windows/).
* Choose install options `Custom installation with unattended access support`,
  `Personal use`, `Show advanced settings`. Untick `Keep me signed in option`
  before login.
* Set options: 
  * `General`: `Start TeamViewer with Windows` (default: enable).
  * `Security`: `Grant you easy access`.
  * `Advanced`: `Check for new version`: `Never`.
  * `Advanced`: `Disable TeamViewer shutdown`.
  * Log out.

#### 5.2. Windows Remote desktop (RDP)

  * `Remote desktop settings`: `Enable remote desktop`.
  * `Computer management`: `Local Users and Groups`: `Groups`: `Remote Desktop Users`: `Add`. ([ref](create-user-and-allow-rdp-permission-on-windows))

### 6. Open listening ports

  * `Windows Defender Firewall`: `Advanced Settings`: `Inbound rules`: `New rule` ([ref](https://vinasupport.com/huong-dan-mo-cong-open-port-tren-windows-server/)).

  * Then go to network modem setting (usually at 192.168.1.1) to map ports.  
    If Firefox gets error `SSL_ERROR_UNSUPPORTED_VERSION`: `security.tls.version.enable-deprecated`. ([ref](https://stackoverflow.com/a/71411721/4097963))  
    Modem settings are usually named DHCP, static IP, Forward Rules.
  
  * Useful commands:
  
  ````
  :: look for value of Ethernet adapter Physical address
  ipconfig /all
  
  :: refresh after config static IP
  ipconfig /release
  ipconfig /renew
  ````

### 7. Install usual apps as admin user

  [Usual apps](https://drive.google.com/drive/folders/1ArpNEL_9r1cseumE0etTTNJBLCixth8i?usp=sharing):
  Git bash, 7z compress, Geany editor, ...
