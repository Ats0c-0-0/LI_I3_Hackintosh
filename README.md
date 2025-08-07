# EFI LI-I3 (Ventura, Sonoma, Sequoia e futuramente Tahoe) 

![only banner](/Images/Banner.png)

**Essa EFI foi feita com ajuda de Deus, muito ChatGPT e OP-Core Simplify.**

Indo direto ao ponto:
- [O que funciona?](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI#o-que-funciona)
  - [Sobre o hackin...](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#sobre-o-hackin)
  - [Lembra quando falei que o Repouso/Sleep funcionava mas tinha um porém? então...](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI#lembra-quando-falei-que-o-repousosleep-funcionava-mas-tinha-um-por%C3%A9m-ent%C3%A3o)
  - [SSDTs feitas no OP-Core (créditos ao cara)](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#ssdts-feitas-no-op-core-cr%C3%A9ditos-ao-cara)
  - [O que deve ser desativado na BIOS?](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#o-que-deve-ser-desativado-na-bios)
- [Maneiras de você criar um bootável do macOS:](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#maneiras-de-voc%C3%AA-criar-um-boot%C3%A1vel-do-macos)
  - [Gerando um novo SMBios](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#gerando-um-novo-smbios)
  - [Observações](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#observa%C3%A7%C3%B5es)
    - [Q&A](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#qa)
- [Agradecimentos](https://github.com/Ats0c-0-0/Lenovo_Ideapad_3i-15IML05-Hackintosh-EFI?tab=readme-ov-file#agradecimentos-aos)

## O que funciona?:

- *Webcam (Lenovo UVC Camera)*
- *Touchpad (ELAN I2C)*
- *HDMI (Audio + Video)*
- *Brightness Control (F11/F12 Keys)*
- *Áudio (mas com alguns problemas, mas sem necessidade de patch's)* 
- *Entrada de cartão de memória (não me pergunte como)*
- *GPU com aceleração gráfica*
- *Gerenciamento de energia da CPU*
- *WiFi/Bluetooth Intel AC9560*
- *Repouso/Sleep funcionando (mas com um porém)*"
- *Boot com Windows 10/11 pelo OpenCore*
- *Thermals*
- *Sensores*
 
## Sobre o hackin...
Compensa usar ele em um IdeaPad com I3? não, mas vai do querer de cada um testar. Na minha opnião, o sistema ficou bom e claro que fica melhor ainda se deixar ele parado iniciando as coisas (parece carro velho), mas não entrega aquilo que ele pode como no Windows _(não me refiro ao 11 e sim ao 10)_.
É bom esperimentar coisas novas como o macOS que é um sistema que não está no alcance de muitos brasileiros pelo fato de um MacBook custar um rim e mais um pouco.

## Lembra quando falei que o Repouso/Sleep funcionava mas tinha um porém? então...
Pelo que testei o sleep funciona, mas tem horas que não e eu não captei esse problema **AINDA**, mas adianto que nem deve correção mesmo pra isso, sempre fica nisso.
Enfim, para funcionar o sleep tem que colocar esse comando no seu terminal :)

`sudo pmset hibernatemode 25 proximitywake 0`

> [!IMPORTANT]
> É de extrema importãncia você dar aquele Reset NVRAM depois de aplicar esse comando

## SSDTs feitas no OP-Core (créditos ao cara)
- SSDT-ALS0
- SSDT-EC
- SSDT-GPI0
- SSDT-MCHC
- SSDT-PLUG
- SSDT-PNLF
- SSDT-RTCAWAC
- SSDT-SBUS
- SSDT-USB-Reset
- SSDT-USBX
- SSDT-XOSI

## O que deve ser desativado na BIOS?
- Todas as configs sobre PXE
- Secure Boot
- Intel SGX
- Flip to boot

# Maneiras de você criar um bootável do macOS:
1. **Maneira demorada, offline e precisa de um PenDrive de 32GB (dependendo da versão, claro)**
  - No site **[olarila.com](https://www.olarila.com/topic/6278-olarila-vanilla-images-macos-installer/)** é disponibilizado algumas imagens de instalação de várias versões do macOS e você vai baixar qualquer versão do macOS Sonoma
  - Faça o flash usando o **[Balena Etcher](https://etcher.balena.io)** ou **[Rufus](https://rufus.ie/pt_BR/)**(lembrando que pelo balena é bem mais demorado)
  - Quando finalizado é só configurar a BIOS e iniciar o pelo PenDrive.
  
2. **Instalador Oficial, maneira mais fácil, porém, precisa de internet (Esse metódo funciona até o macOS Sonoma)**
  - Baixe o **[macrecovery](https://github.com/luchina-gabriel/macrecovery)** e descompacte o zipado
  - Vá nessa [página](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install-recovery.html#:~:text=Instructions%20for%20running%20are%20quite%20simple%2C%20choose%20from%20one%20of%20the%20below%20commands%20depending%20on%20which%20OS%20you%20want%20to%20download%3A), procure a versão que deseja, abra o cmd ou terminal dentro da pasta do macrecovery e execute o código
  - Formate o seu PenDrive em FAT32 e crie a pasta `com.apple.recovery.boot`, mova os arquivos baixados para essa pasta e a EFI para a raiz do PenDrive e pronto, você tem um instalador legacy original em seu PenDrive.

>[!NOTE]
> Se caso você tem tentar baixar a imagem de recuperação pelo macrecovery e o cmd do Windows dizer que o python não estiver instalado, use python ao invés de python3
  
## Gerando um novo SMBios
No meu ponto de vista não tem app melhor pra fazer isso do que o **[OCAT (OCAuxiliaryTools)](https://github.com/ic005k/OCAuxiliaryTools/releases)** e aqui vou te ensinar como você vai gerar as novas informações

Abra o app e clique no 3º icone da direita para esquerda, monte sua EFI que está no PenDrive, vá em PI que está na barra lateral com um icone de iMac e clique no botão generate de SystemProductName (não se esqueça de checar se o SystemSerialNumber é real, lembre-se que ele não deve ser)
> SMBios que deve ser usada e do `MacBookPro16,2`

## Observações
- SecureBootModel foi configurado para `disabled` para evitar problemas com atualização e upgrade de versões de sistema e com isso vem um problema de travar no meio das atualizações e para resolver isso bastar você reiniciar e resetar a NVRAM e tente novamente.

- Antes o `alcid=11`funcionava bem, mas devido atualizações acabou perdendo o suporte a entrada AUX e única id que funciona hoje em dia é a `alcid=100`

### Q&A
- Posso usar o meu CPUFriendFriend?
  - Sim e deve

- Posso modificar as portas USBs
  - Não, pois já está configurada para evitar problemas com sleep

- Posso mudar o SecureBootModel para ativado (default)
  - Pode!

- Posso usar seu projeto para trazer suporte para outro IdeaPad 3i?
  - Sim!! só não esqueça de colocar os devidos créditos

>[!CAUTION]
> Pelo amor de Deus, não mude a SMBios atoa porque isso vai quebrar as configurações das portas USB

# Agradecimentos ao
- [Acidanthera](https://github.com/acidanthera) por [OpenCore](https://github.com/acidanthera#:~:text=of%2047%20repositories-,OpenCorePkg,-Public) e também por:
  - [AppleALC](https://github.com/acidanthera/AppleALC)
  - [Whatevergreen](https://github.com/acidanthera/WhateverGreen)
  - [VirtualSMC](https://github.com/acidanthera/VirtualSMC)
  - [Lilu](https://github.com/acidanthera/Lilu)
  - [RestrictEvents](https://github.com/acidanthera/RestrictEvents)
  - [HibernationFixup](https://github.com/acidanthera/HibernationFixup)
  - [NVMeFix](https://github.com/acidanthera/NVMeFix)
  - [CpuTscSync](https://github.com/acidanthera/CpuTscSync)
  - [CPUFriend](https://github.com/acidanthera/CPUFriend)
  - [VoodooPS2](https://github.com/acidanthera/VoodooPS2)
  - [MaciASL](https://github.com/acidanthera/MaciASL)
  - [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys)
  - [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM)
- [OpenIntelWireless](https://github.com/OpenIntelWireless) por [AirportItlwm, Itlwm](https://github.com/OpenIntelWireless/itlwm) e por [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
- [Corpnewt](https://github.com/corpnewt) por [CPUFriendFriend](https://github.com/corpnewt/CPUFriendFriend) e [USBMap](https://github.com/corpnewt/USBMap)
- [Averycblack](https://github.com/averycblack) por [ECEnabler](https://github.com/averycblack/ECEnabler)
- [VoodooI2C](https://github.com/VoodooI2C) por [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C)[^1] 
- Queridissimo Deus por não ter feito eu desistir e me jogar na frente do caminhão
- ChatGPT que ajudou demais com explicações e pesquisas
- OP-Core Simplify que ajudou a criar as SSDT

[^1]: KKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK