# HACKINTOSH-EFI-INTEL-13TH-13600K-B760M-DDR5-RX5700XT

>⛓ [Link to the original repository](https://github.com/luchina-gabriel/BASE-EFI-INTEL-DESKTOP-13THGEN-RAPTOR-LAKE)

>🔧 _Based on Opencore 0.9.2_

> 🖥️ SmBIOS - iMacPro1,1

This EFI was developed for the following hardware:
- **CPU**: Intel Core i5 13th - 13600k
- **Mainboard**: Gigabyte B760M Aorus Elite DDR5 (rev. 1.0)
- **GPU**: AMD Radeon RX5700 XT - 8GB (Asus TUF)
- **Memory**: XPG Lancer DDR5@5200 MHz - (2x16Gb) 
- **Wireless Card**: Fenvi t919 (bcm94360)
- **Storage**: KingSpec NMVE NE2280 PCIe Gen3 x4

## Features
- [x] USB Map
- [x] Custom ACPI Tables
- [x] Boot Shine
- [x] Built-in Network cards
- [x] Built-in Sound cards
- [x] CPU Name
- [x] GPU Name
- [ ] Sleep crashs ``in Progress``

## Kexts used (included)
Kext|Description
:----|:----
[Lilu.kext](https://github.com/acidanthera/Lilu/releases)|Patch many processes, required for AppleALC, WhateverGreen, VirtualSMC and many other kexts.
[SMCProcessor.kext](https://github.com/acidanthera/VirtualSMC/releases)|Used for monitoring CPU temperature, doesn't work on AMD CPU based systems.
[SMCSuperIO.kext](https://github.com/acidanthera/VirtualSMC/releases)|Used for monitoring fan speed, doesn't work on AMD CPU based systems.
[VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases)|Emulates the SMC chip found on real macs, without this macOS will not boot.<br>Alternative is FakeSMC which can have better or worse support, most commonly used on legacy hardware.
[WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)|Used for graphics patching, DRM fixes, board ID checks, framebuffer fixes, etc; all GPUs benefit from this kext.
[AppleALC.kext](https://github.com/acidanthera/AppleALC/releases)|Used for AppleHDA patching, allowing support for the majority of on-board sound controllers.<br>AMD 15h/16h may have issues with this and Ryzen/Threadripper systems rarely have mic support.
[LucyRTL8125Ethernet.kext](https://www.insanelymac.com/forum/files/file/1004-lucyrtl8125ethernet/)|For Realtek's 2.5Gb Ethernet.
[NVMeFix.kext](https://github.com/acidanthera/NVMeFix/releases)|Used for fixing power management and initialization on non-Apple NVMe.
[RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents/releases)|Better experience with unsupported processors like AMD, Disable MacPro7,1 memory warnings and provide upgrade to macOS Monterey via Software Updates when available.
[CpuTscSync.kext](https://github.com/acidanthera/CpuTscSync/releases)|It is a Lilu plugin, combining functionality of VoodooTSCSync and disabling xcpm_urgency if TSC is not in sync. It should solve some kernel panics after wake.
[USBWakeFixup.kext](https://github.com/osy/USBWakeFixup)|This extension is a workaround for that issue by creating a fake ACPI device with the right wakeup params.
USBMap.kext|Kext generated after mapping the USB ports

## Tools

Tool|Description
:----|:----
[ProperTree](https://github.com/corpnewt/ProperTree) | Configure config.plist
[USBMap](https://github.com/corpnewt/USBMap) | Making the USB Map
[gibMacOS](https://github.com/corpnewt/gibMacOS) | Download and create macOS images
[SSDTTime](https://github.com/corpnewt/SSDTTime) | M ake creating SSDTs simple
[CPU-Name](https://github.com/corpnewt/CPU-Name) | Fix the cpu name
[MountEFI](https://github.com/corpnewt/MountEFI) | Shortcut to Mount the EFI Driver
[gibMacRecovery](https://github.com/corpnewt/gibMacRecovery) | Download and create macOS recoverys
[gebSMBIOS](https://github.com/corpnewt/GenSMBIOS) | Generate information from SMBIOS
[IORegistryExplorer](https://github.com/vulgo/IORegistryExplorer) | Validate information regarding hardware power management
[iASL](https://www.acpica.org/downloads) | Change and convert SSDTs (for Windows)
[Mac iASL](https://github.com/acidanthera/MaciASL) | Change and convert SSDTs (for MAC)
[OpenCore-Packager](https://github.com/chris1111/OpenCore-Packager) | Tool that assists in the installation of the EFI in a simple way

## Softwares

- [Stats](https://github.com/exelban/stats)
- [Hackintool](https://github.com/benbaker76/Hackintool)

## BIOS Settings
> Bios Version: **F11a**
* **Tweaker**
  * Advanced CPU Settings
    * Hyper Threading Technology - ``Enabled``
* **Settings**
  * Plataform Power
    * PEG ASPM - ``Enabled``
    * PCH APSM - ``Enabled``
    * DMI ASPM - ``Enabled``
    * Native ASPM - ``Enabled``
    * Power Loading - ``Enabled``
  * IO Ports
    * Internal Graphics - ``Disabled``
    * Above 4G Decoding - ``Enabled``
    * Above 4GB MMIO Bios Assignment - ``Enabled``
    * Re-Size Bar Support - ``Disabled``
    * USB Configuration
      * XHCI Hand-Off - ``Enabled``
    * VMD Setup Menu
      * VMD Controller - ``Disabled``
  * **Miscellaneous**
    * Intel Plataform Trust Technology (PTT) - ``Enabled``
    * VT-d - ``Enabled``
* **Boot**
  * CFG Look - ``Disabled``
  * Fast boot - ``Enabled``
  * Windows 10 Features - ``Windows 10``
  * CSM Support - ``Enabled``

## Useful Links
- [Dortania Getting Started](https://dortania.github.io/getting-started/)
- [Dortania Troubleshooting](https://dortania.github.io/troubleshooting/)
- [Dortania Post Install](https://dortania.github.io/OpenCore-Post-Install/)
- [Dortania Documentation](https://dortania.github.io/docs/)

> ## Warnings ⚠️
> - Instalar primeiramente o macOS Catalina para realizar o mapeamento das portas. Posteriormente instalar versões mais atuais.
> - Sempre realize a instalação utilizando rede cabeada
> - Configurar o AppleID somente ao fim do processo
> - A cada alteração na EFI após a instalação, fazer o backup. Se possível, versionar no Git.
> - Para validar se as kexts estao executando → `kextstat | greep-v com.apple`
> - Para desabilitar bloqueio de apps não autorizados → `sudo spctl —master -disable`

<details><summary><h2>Install Guide</h2></summary><p>

  ## Pre Install

 - Levantar as Especificações

     Utilizando o AIDA64, realizar o levantamento das seguintes informações abaixo

     - CPU
     - Chipset
     - GPU
     - Placa de rede
     - Codec Placa de Audio
     - Controladora USB
 - Baixar arquivos necessários
     - Python
     - EFI Base
     - ProperTree
     - MountEFI
     - genSMBIOS
     - Kexts necessárias não incluídas
     - ACPI Tables Prebuilt
 - Criar SSDTs


 - Instale o Python
     - lembrando de marcar a opção de `ADD Python to PATH`
 - Baixar Recovery
     - Extrair EFI baixada do diretório base
     - Acessar o diretório na EFI `.\Utils\macrecovery\`
     - Abrir arquivo `.\recovery_urls.txt` e copiar código da versão do macOS escolhida.
     - Executar um prompt do CMD no caminho atual e colar o código copiado.
     - Após executar o comando, serão baixados dois arquivos num diretório chamado `com.apple.recovery.boot`: `BaseSystem.chucklist` e `BaseSystem.dmg`
     - A estrutura final do diretório deve ser a seguinte

         ```bash
         - EFI
             - BOOT
             - OC
                 - ACPI
                 - Drivers
                 - Kexts
                 - Resources
                 - Tools
             - com.apple.recovery.boot
           - Utils
         ```

 - Criar estrutura de pastas
     - Formatar o disco que será utilizado como FAT32
     - Dentro do disco coloque os seguintes arquivos:
         - Copiar e colar a pasta `com.apple.recovery.boot` baixada no `.\Utils\macrecovery\`
         - Copiar e colar a pasta `EFI-Release` e renomear para `EFI`
             - Colar Kexts baixadas no seguinte diretório `EFI\OC\Kexts\`
             - Colar arquivos de `.aml` das tables baixadas no seguinte diretório `EFI\OC\ACPI\`
         - Criar a pasta `Utils` para guardar as ferramentas que serão utilizadas pós instalação
             - MountEFI
             - ProperTree
 - Gerar a `SMBIOS`
     - Descompactar o arquivo baixado da SMBIOS
     - Executar o arquivo `genSMBIOS.bat`
     - Escolher a opção `3 GENERATE SMBIOS`
     - Incluir a versão da SMBIOS que será utilizada, conforme documentação. Ex: `iMAC20,2`
     - Copiar informações Geradas:
         - Type
         - Serial
         - BoardSerial
         - SmUUID
         - Apple ROM
     - Encerrar APP
 - Configurando o `config.plist`
     - Descompactar o `ProperTree` para configuração do arquivo `config.plist`
     - Executar o arquivo `ProperTree.bat`
     - Pressione `Ctrl + O`, para carregar o arquivo `config.plist`
     - Navegue ate o seguinte diretório no disco `EFI\OC\` e selecione o arquivo `config.plist`
     - Após abrir o arquivo, navegue ate o seguinte caminho `PlataformInfo > Generic` e configure os seguintes campos conforme os dados gerados da SMBIOS
         - `Type` = `SystemProductName`
         - `Serial` = `SystemSerialNumber`
         - `BoardSeria`l = `MLB`
         - `SmUUID` = `SystemUUID`
         - `Apple ROM` = `ROM`
     - Após preencher os dados, o arquivo `config.plist` precisa ser reprocessado para garantir as informações alteradas , as kexts e ACPI tables incluídas . Para isso, clique no menu `File - OC Clean Snapshot` e selecione o diretório `EFI\OC\` do Pen Drive.
     - Após o primeiro rebuild e carregamento de todas as kexts, validar os pontos de atenção disponíveis na documentação e fazer a configuração no arquivo `config.plist`
     - Após concluir, acessar o menu `File - Save` para salvar as alterações e prosseguir com o processo
 - Configurar BIOS conforme documentação

 ### Install

 - Bootar Pen Drive para iniciar a instalação
 - Escolher o disco do OpenCore
 - Após carregar instalador do SO, acessar o app Disc Utility
 - Formatar o disco que será usado conforme as seguintes detalhes:
     - Formato → APFS
     - Scheme → GUID Partition MAP
     - Nome → macOS
 - Após formatar o disco, abrir o safari para confirmar se existe rede disponível.
 - Prosseguir com a instalação

 ### Pos Install

 - Mapear portas USB
     - Baixar USBMap
     - Executar
     - Realizar o Discovery das portas
     - Identificar cada porta
 - Corrigir `Built-in` das Placas de Redes
     - Validar no app Hackintool se o flag `built-in` esta habilitado em todas as interfaces de rede
     - Caso não esteja, copiar o device path da placa de rede
     - Abra o `config.plist` e no seguinte caminho `DeviceProperties\Add`, faça as seguintes modificações:
         - Crie um novo item e cole o path
         - Altere o tipo do item para `Dictionary`
         - Crie uma string filha no item criado com o nome `built-in` e mude para o tipo `data`
         - em `built-in` coloque o valor `01000000`
         - Repita com todas as interfaces que rede que não estiverem com o `built-in` ativado
         - Salve e reinicie a maquina
 - Configurar Áudio
     - Identifique o Codec de áudio utilizado pela placa mãe
     - Baixar e instalar kext correspondente
     - Incluir os layouts da placa de áudio no `boot-args` do `config.plist` conforme codec suportado. →  https://github.com/acidanthera/AppleALC/wiki/Supported-codecs
     - Após a identificação do Codec acesse o app `Hackintool > PCIe` e pesquise pela placa de som.
     - Copie o device PATH da placa de som
     - Abra o `config.plist` e no seguinte caminho `DeviceProperties\Add`, faça as seguintes modificações:
         - Crie um novo item e cole o path
         - Altere o tipo do item para `Dictionary`
         - Crie uma string filha no item criado com o nome `layout-id` e mude para o tipo `number`
         - em `layout-id` coloque o valor do layout identificado
         - Remova o layout no que foi inserido no `boot-args`
         - Salve e reinicie a maquina
 - Configurar Som de Inicio
     - Copiar o path da placa de áudio
     - Acessar o `config.plist` e fazer as seguintes modificações em `UEFI\Audio`
         - `AudioDevice → [Path da placa de Audio]`
         - `AudioSupport → true`
         - `AudioOutMask → -1`
 - Ajustes estéticos no `config.plist`
     - `PickerAtributes → 17` - Modo Gráfico Open Core
     - `PickerMode → External` - Modo gráfico Open Core
     - `PollAppleHotKeys → True` - Habilita atalhos de boot no teclado como nos macs Originais
     - `PickerVariant → Auto` - Tema dos ícones do menu do Open Core
     - `HideAuxiliary → True` - Exibe somente os discos de SO no menu do Open Core (Para exibir as demais opções, pressione espaço e habilite `PollAppleHotKeys`
     - `Timeout → 5` - Tempo em segundos que o menu do Open Core vai ficar aberto
     - `ShowPicker → false` - Oculta o menu do Open Core
     - `LauncherOption → Full` - Migração da EFI para o disco do PC
     - `RequestBootVarRouting → True`  - Migração da EFI para o disco do PC
     - `ScanPolicy → 2687747` → Oculta os discos de Windows do menu de boot do Open Core
 - Instalar EFI
     - Basta baixar o app OpenCore Packager
 - CPU Name
     - Baixar app CPU_Name
     - Incluir o arrastar o config.plist para o CMD.
 - Corrigir problemas de Sleep
</p></details>


