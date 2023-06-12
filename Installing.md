
> ## Warnings ⚠️
> - Instalar primeiramente o macOS Catalina para realizar o mapeamento das portas. Posteriormente instalar versões mais atuais.
> - Sempre realize a instalação utilizando rede cabeada
> - Configurar o AppleID somente ao fim do processo
> - A cada alteração na EFI após a instalação, fazer o backup. Se possível, versionar no Git.
> - Para validar se as kexts estao executando → `kextstat | greep-v com.apple`
> - Para desabilitar bloqueio de apps não autorizados → `sudo spctl —master -disable`

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
