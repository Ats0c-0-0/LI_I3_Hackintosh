# EFI LI-I3 (Sonoma até agora) 

![only banner](/Images/Banner.png)

### Essa EFI foi feita com ajuda de Deus, muito ChatGPT e OP-Core Simplify.

**EFI foi refeita do zero para maior compatibilidade com o notebook**

## <br/>O que funciona?:<br>

  - *Webcam (Lenovo UVC Camera)*
  - *Touchpad (ELAN I2C)*
  - *HDMI (Audio + Video)*
  - *Brightness Control (F11/F12 Keys)*
  - *Entrada de cartão de memória (não me pergunte como)*
  - *GPU com aceleração gráfica*
  - *WiFi/Bluetooth Intel AC9560*
  - *Repouso/Sleep funcionando (mas com um porém)*"
  - *Thermals*
  - *Sensores*
<br><br/>
 
## Sobre o hackin...
Compensa usar ele em um IdeaPad com I3? não, mas vai do querer de cada um testar. Na minha opnião, o sistema ficou bom e claro que fica melhor ainda se deixar ele parado iniciando as coisas (parece carro velho), mas não entrega aquilo que ele pode como no Windows _(não me refiro ao 11 e sim ao 10)_.
É bom esperimentar coisas novas como o macOS que é um sistema que não está no alcance de muitos brasileiros pelo fato de um MacBook custar um rim e mais um pouco.

## Lembra quando falei que o Repouso/Sleep funcionava mas tinha um porém? então...
Pelo que testei o sleep funciona, mas tem horas que não e eu ainda não captei esse problema **AINDA**, mas adianto que nem deve correção mesmo pra isso, sempre fica nisso.
Enfim, para funcionar o sleep tem que colocar esse pequeno comando no seu terminal :)

`sudo pmset hibernatemode 25 womp 0 sleep 1 ttyskeepawake 1 && sudo pmset displaysleep 0 halfdim 0 tcpkeepalive 1 standby 1 powernap 1`

### Atualização sobre Sleep/Repouso (01/08/25)
Feito alguns testes e agora funciona bem até com esse novo comando

> [!IMPORTANT]
> É de extrema importãncia você dar aquele Reset NVRAM depois de aplicar esse comando

## <br/>SSDTs feitas no OP-Core (créditos ao cara)<br>
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

## <br/>O que deve ser desativado na BIOS?<br>
- Todas as configs sobre PXE
- Secure Boot
- Intel SGX
- Flip to boot

# <br/>Maneiras de você criar um bootável do macOS:<br>
1. **Maneira rápida, prática e offline**
   - No site **[olarila.com](https://www.olarila.com/topic/6278-olarila-vanilla-images-macos-installer/)** é disponibilizado algumas imagens de instalação de várias versões do macOS e você vai baixar qualquer versão do macOS Sonoma
   - Faça o flash usando o **[Balena Etcher](https://etcher.balena.io)** ou **[Rufus](https://rufus.ie/pt_BR/)**(lembrando que pelo balena é bem mais demorado)
   - Quando finalizado é só configurar a BIOS e iniciar o pelo PenDrive.
  
2. **Maneira mais fácil, mas precisa de internet no instalador (Installer Legacy)**
   - Baixe o **[macrecovery](https://github.com/luchina-gabriel/macrecovery)** e descompacte o zipado
   - Dentro da pasta, execute esse código `python3 ./macrecovery.py -b Mac-226CB3C6A851A671 -m 00000000000000000 download`
   - Formate o seu PenDrive em FAT32 e crie a pasta `com.apple.recovery.boot`, mova os arquivos baixados para essa pasta e a EFI para a raiz do PenDrive e pronto, você tem um instalador legacy original em seu PenDrive.

>[!NOTE]
>Independente do metodo que for usar você vai precisar de um PenDrive com bastante espaço 
  
## <br/>Gerando um novo SMBios<br>
No meu ponto de vista não tem app melhor pra fazer isso do que o **[OCAT (OCAuxiliaryTools)](https://github.com/ic005k/OCAuxiliaryTools/releases)** e aqui vou te ensinar como você vai gerar as novas informações.

Abra o app e clique no 3º icone da direita para esquerda, monte sua EFI que está no PenDrive, vá em PI que está na barra lateral com um icone de iMac e clique no botão generate de SystemProductName (não se esqueça de checar se o SystemSerialNumber é real, lembre-se que ele não deve ser)
> SMBios que deve ser usada e do `MacBookPro16,2`

>[!CAUTION]
> Pelo amor de Deus, não mude a SMBios atoa porque isso vai quebrar as configurações das portas USB

# Agradecimentos
  - Primeiramente a Deus por não ter feito eu desistir e me jogar na frente do caminhão
  - Ao ChatGPT que ajudou demais com explicações e pesquisas
  - E ao OP-Core Simplify que ajudou a criar as SSDT