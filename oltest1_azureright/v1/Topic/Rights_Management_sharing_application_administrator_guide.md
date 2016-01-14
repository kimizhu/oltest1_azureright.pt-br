---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Guia do administrador do aplicativo de compartilhamento Rights Management
Use as seguintes informações se você for responsável pelo aplicativo de compartilhamento Microsoft Rights Management em uma rede corporativa, ou se você quiser obter mais informações técnicas do que há em [Guia do usuário do aplicativo de compartilhamento Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md) ou [perguntas Frequentes para aplicativo de compartilhamento Microsoft Rights Management para Windows](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [Implantação automática para os aplicativos de compartilhamento do Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [Verificando o sucesso da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Comandos de desinstalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Suprimindo atualizações automáticas](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Apenas Azure RMS: Configurando o controle de documentos](#BKMK_DocumentTracking)

    -   [Somente AD RMS: Suporte para vários domínios de email dentro de sua organização](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Visão geral técnica do aplicativo de compartilhamento Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Níveis de proteção - nativo e genérico](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Tipos de arquivo com suporte e extensões de nome de arquivo](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Alterando o nível de proteção padrão de arquivos](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Se você for novo no aplicativo de RMS sharing ou procura mais informações, consulte [Como o RMS protege todos os tipos de arquivo – usando o aplicativo RMS sharing](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

O aplicativo de RMS sharing é ideal para trabalhar com o Azure RMS, porque essa configuração de implantação oferece suporte ao envio de anexos protegidos aos usuários de outra organização, e opções como notificações por email e controle de documento com revogação.  No entanto, com algumas limitações, também funciona com a versão local, AD RMS. Para obter uma comparação abrangente dos recursos que são suportados pelo Azure RMS e o AD RMS, consulte [Comparando o Azure Rights Management e o AD RMS](https://technet.microsoft.com/library/jj739831.aspx). Se você tiver o AD RMS e deseja migrar para o Azure RMS, consulte [Migrando do AD RMS para o Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>Implantação automática para os aplicativos de compartilhamento do Microsoft Rights Management
A versão do Windows do aplicativo de RMS sharing oferece suporte a uma instalação com script, o que a torna adequada para implantações corporativas.

Os únicos pré-requisitos para as instalações são que os computadores executem uma versão mínima do Windows 7 Service Pack 1 e o Microsoft Framework, versão mínima 4.0 esteja instalada. Se você precisar instalar o Microsoft .NET Framework 4.0, você pode [baixá-lo para instalação do Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=17718).

#### Para baixar o aplicativo RMS sharing para implantação automática

1.  Vá para a página do[aplicativo de compartilhamento Microsoft Rights Management para Windows](http://www.microsoft.com/download/details.aspx?id=40857) no Microsoft Download Center e clique em **Baixar**.

2.  Selecione e baixe os arquivos que você precisa. Existem dois pacotes de instalação de cliente: um para Windows 64 bits (aplicativo de compartilhamento Microsoft Rights Management x64.zip) e outro para Windows de 32 bits (aplicativo de compartilhamento Microsoft Rights Management x86.zip).

3.  Extraia os arquivos dos pacotes de instalação compactados, por exemplo, clicando duas vezes neles. Em seguida, copie os arquivos extraídos para um local de rede que os computadores clientes possam acessar.

Os pacotes de instalação para o aplicativo de RMS sharing oferece suporte a diferentes cenários de implantação e inclui o seguinte:

|Descrição|Cenário de implantação|
|-------------|--------------------------|
|Assistente de Conexão do Microsoft Online|Exigido para os seguintes:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2013 e Azure RMS se você não tiver instalado a atualização para o Office 2013 de [9 de junho de 2015](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Hotfix para Office (KB 2596501)|Exigido para os seguintes:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS|
|Hotfix para habilitar o cliente AD RMS 1.0 para trabalhar com o Azure RMS (2843630 KB)|Exigido para os seguintes:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS|
|Cliente AD RMS e o aplicativo RMS sharing|Exigido para os seguintes:<br /><br />-   Office 2016 ou Office 2013 e Azure RMS ou Active Directory RMS<br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS<br />-   Apenas o aplicativo RMS sharing e suplemento do Office|
|Suplemento do Office para a faixa de opções|Exigido para os seguintes:<br /><br />-   Office 2016 ou Office 2013 e Azure RMS ou Active Directory RMS<br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS<br />-   Apenas o aplicativo RMS sharing e suplemento do Office|
|Ferramenta de Preparação do Rights Management do Active Directory do Azure|Exigido para os seguintes:<br /><br />-   Office 2010 e Azure RMS|
Use os procedimentos a seguir para identificar os comandos necessários para implantar o aplicativo RMS sharing para esses cenários de implantação:

-   **Office 2016 ou Office 2013 e Azure RMS ou Active Directory RMS**

    Seus usuários estão executando o Office 2016 ou Office 2013, sua organização usa o Azure RMS ou o Active Directory RMS e os usuários colaboram com outras organizações que usam o Azure RMS ou Active Directory RMS.

-   **Office 2010 e Azure RMS**

    Seus usuários estão executando o Office 2010, sua organização usa o Azure RMS, e os usuários colaboram com outras organizações que usam o Azure RMS ou Active Directory RMS.

-   **Office 2010 e Active Directory RMS**

    Seus usuários estão executando o Office 2010, sua organização usa o AD RMS, e os usuários colaboram com outras organizações que usam o Azure RMS.

-   **Apenas o aplicativo RMS sharing e suplemento do Office**

    Seus usuários estão executando o Office 2016, Office 2013 ou o Office 2010, sua organização usa o AD RMS, e os usuários não precisam colaborar com outras organizações que usam o Azure RMS. Essa instalação permite que você instale apenas o aplicativo de compartilhamento e o suplemento do Office.

> [!NOTE]
> Nesses cenários, se a sua organização está executando o AD RMS, seus usuários poderão receber conteúdo protegido de outras organizações que usam o Azure RMS, mas os seus usuários não podem enviar conteúdos protegidos aos usuários em uma organização que usa o Azure RMS. No entanto, se sua organização estiver executando o Azure RMS, os seus usuários podem enviar e receber conteúdo protegido de outras organizações.

Para concluir a instalação para cada procedimento, o computador deve ser reiniciado. Você pode iniciar uma reinicialização automática usando um comando como shutdown /i.

#### Para implantar o aplicativo RMS sharing para Office 2016 ou o Office 2013 e o Azure RMS ou Active Directory RMS

-   Em cada computador no qual você deseja instalar o aplicativo RMS sharing e componentes relacionados, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s
    ```

Para verificar o sucesso, consulte a seção [Verificando o sucesso da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) neste tópico.

#### Para implantar o aplicativo RMS sharing para Office 2010 e o Azure RMS

1.  Você deve ser o administrador global para seu locatário Office 365 ou Azure Active Directory para que você possa obter a URL do serviço de certificação da sua organização, executando a ferramenta de preparação do Azure Active Directory Rights Management. Você precisa executar essa ferramenta apenas uma vez em um único computador. Você usará a URL do serviço de certificação em cada computador em que instalar o aplicativo de RMS sharing:

    1.  Fazer logon em um computador usando uma conta de administrador local.

    2.  Nesse computador, [baixe e instale o Assistente de conexão Microsoft Online](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Execute o seguinte comando para ver exibida na tela a URL de serviço de certificação, que você pode copiar e salvar para a próxima etapa:

        -   Para Windows 8.1 e Windows 8, 64 bits:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Para Windows 8.1 e Windows 8, 32 bits:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Para o Windows 7, 64 bits:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Esse comando pode solicitar que você insira suas credenciais do Azure. Se o computador não tiver ingressado em um domínio, você será solicitado. Se o computador tiver ingressado em um domínio, a ferramenta poderá usar credenciais armazenadas em cache.

2.  Em cada computador no qual você deseja instalar o aplicativo RMS sharing, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Em cada computador no qual você deseja instalar o aplicativo RMS sharing, os usuários devem executar o seguinte comando (não necessita de privilégios elevados). Há diferentes maneiras de alcançar isso, incluindo pedir aos usuários para executar o comando (por exemplo, um link em uma mensagem de email ou um link no portal help desk) ou você pode adicioná-lo para o script de logon:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Para verificar o sucesso, consulte a seção [Verificando o sucesso da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) neste tópico.

#### Para implantar o aplicativo RMS sharing para Office 2010 e o Active Directory RMS

1.  Em cada computador no qual você deseja instalar o aplicativo RMS sharing, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Em cada computador no qual você deseja instalar o aplicativo RMS sharing, os usuários devem executar o seguinte comando (não necessita de privilégios elevados). Há diferentes maneiras de alcançar isso, incluindo pedir aos usuários para executar o comando (por exemplo, um link em uma mensagem de email ou um link no portal help desk) ou você pode adicioná-lo para o script de logon:

    -   Para Windows 10, Windows 8.1 e Windows 8, 64 bits:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Para Windows 10, Windows 8.1 e Windows 8, 32 bits:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Para o Windows 7, 64 bits:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Para verificar o sucesso, consulte a seção [Verificando o sucesso da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) neste tópico.

#### Para instalar apenas o aplicativo RMS sharing e suplemento do Office

1.  Instale o cliente AD RMS e o aplicativo RMS sharing usando o seguinte comando:

    -   Para o Windows 64 bits:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Para o Windows 32 bits:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Instale o suplemento do Office usando os seguintes comandos:

    -   Para versões 64 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Para versões 32 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Para verificar o sucesso, consulte a seção [Verificando o sucesso da instalação](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) neste tópico.

### <a name="BKMK_verifyscripted"></a>Verificando o sucesso da instalação
Você pode usar os arquivos de log da instalação para verificar uma instalação bem-sucedida.

##### Para verificar o sucesso da instalação para o aplicativo RMS sharing para Office 2016 ou o Office 2013 e o Azure RMS ou Active Directory RMS

-   Para verificar o sucesso do comando Setup.exe, em cada computador, procure o arquivo de log da instalação **RMInstaller.log** na pasta *%temp%\RMS_installer_&lt;guid&gt;* e, em seguida, identifique o código de saída.

    Uma instalação bem sucedida tem o código de saída 0 e qualquer outro número indica uma falha na instalação.

    Exemplo de nome do arquivo de log: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### Para verificar o sucesso da instalação para o aplicativo RMS sharing para Office 2010 e Azure RMS

1.  Para verificar o sucesso do comando Setup.exe, em cada computador, procure o arquivo de log da instalação **RMInstaller.log** na pasta *%temp%\RMS_installer_&lt;guid&gt;* e, em seguida, identifique o código de saída.

    Uma instalação bem sucedida tem o código de saída 0 e qualquer outro número indica uma falha na instalação.

    Exemplo de nome do arquivo de log: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Para verificar o sucesso do comando RMSSetup.exe, o usuário deve ter os seguintes arquivos criados na sua pasta *%localappdata%\microsoft\drm*:

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Exemplo de arquivo CLC-&#42;.drm:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

##### Para verificar o sucesso da instalação para o aplicativo RMS sharing para Office 2010 e Active Directory RMS

1.  Para verificar o sucesso do comando Setup.exe, em cada computador, procure o arquivo de log da instalação na pasta *%temp%\RMS_installer_&lt;guid&gt;* e identifique o código de saída.

    Uma instalação bem sucedida tem o código de saída 0 e qualquer outro número indica uma falha na instalação.

    Exemplo de nome do arquivo de log: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Para verificar o êxito do comando aadrmprep.exe, em cada computador, procure o seguinte texto no arquivo de log da instalação: **aadrmprep.exe foi encerrado com o status de SUCESSO**

    > [!NOTE]
    > Às vezes, a instalação pode executar duas vezes; a primeira ocorrência falhará e a segunda é bem-sucedida.

    Se você quiser verificar manualmente as alterações no registro que essa ferramenta faz, eles são os seguintes:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

##### Para verificar o sucesso da instalação apenas para o aplicativo RMS sharing e suplemento Office

1.  Para verificar o sucesso do comando Setup_ipviewer.exe, procure o seguinte texto no arquivo de log da instalação: **Status de sucesso ou erro na instalação: 0**

    Linhas de exemplo de uma instalação bem-sucedida:

    **MSI (s) (F0:B8) [14:19:57:854]: Produto: Active Directory Rights Management Services Client 2.1 - Instalação concluída com sucesso.**

    **MSI (s) (F0:B8) [14:19:57:854]: O Instalador do Windows instalou o produto. Nome do produto: Active Directory Rights Management Services 2.1. Versão do produto: 1.0.1179.1. Idioma do produto: 1033. Fabricante: Microsoft Corporation. Status de sucesso ou erro na instalação: 0.**

2.  Para verificar o sucesso do suplemento do Office, em cada computador, procure o seguinte texto no arquivo de log da instalação: **Status de sucesso ou erro na instalação: 0**

    Linhas de exemplo de uma instalação bem-sucedida:

    **MSI (s) (9C:88) [18:49:04:007]: Produto: Suplementos do Microsoft RMS Office -- Instalação concluída com êxito.**

    **MSI (s) (9C:88) [18:49:04:007]: O Instalador do Windows instalou o produto. Nome do produto: Suplementos do Microsoft RMS Office. Versão do produto: 1.0.7. Idioma do produto: 1033. Fabricante: Microsoft. Status de sucesso ou erro na instalação: 0.**

### <a name="BKMK_uninstallscripted"></a>Comandos de desinstalação
Nem todos os comandos de instalação que são necessários para essas implantações oferecem suporte a um comando de desinstalação. Você pode desinstalar o cliente AD RMS e o aplicativo de compartilhamento, e você pode desinstalar o suplemento do Office. Use os seguintes comandos para desinstalar esses elementos.

##### Para desinstalar o Cliente AD RMS e o aplicativo RMS sharing

-   Execute os seguintes comandos:

    -   Para o Windows 64 bits:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Para o Windows 32 bits:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### Para desinstalar o suplemento do Office

-   Execute os seguintes comandos:

    -   Para versões 64 bits do Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Para versões 32 bits do Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Suprimindo atualizações automáticas
Como padrão, os usuários são notificados se houver uma versão posterior do aplicativo de compartilhamento do RMS e solicitados a baixá-lo. Você pode suprimir esta notificação fazendo a seguinte edição no registro:

1.  Navegue até **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e, se não estiver presente, crie uma nova chave chamada **RmsSharingApp**.

2.  Selecione **RmsSharingApp**, crie um novo valor DWORD de **AllowUpdatePrompt**, e defina o valor como **0**.

Embora o aplicativo RMS sharing não seja suportado pelo WSUS, você pode usar a técnica a seguir para testar qualquer novas versões do aplicativo RMS sharing antes de implantá-lo em todos os usuários:

1.  Nos computadores de todos os usuários, execute um script para suprimir as atualizações automáticas. Nos computadores usados pelos administradores para testar as novas versões, não execute esse script.

2.  Quando uma nova versão estiver disponível, os administradores a baixarão e a testarão.

3.  Quando o teste for concluído e quaisquer problemas resolvidos, implante a versão mais recente para todos os usuários usando as instruções de implantação automática neste guia.

### <a name="BKMK_DocumentTracking"></a>Apenas Azure RMS: Configurando o controle de documentos
Se você tiver uma [assinatura que oferece suporte a controle de documento](https://technet.microsoft.com/en-us/dn858608), o site de controle de documento é habilitado como padrão para todos os usuários em sua organização.  O controle de documento mostra informações como os endereços de email das pessoas que tentaram acessar documentos protegidos que os usuários compartilharam, quando essas pessoas tentavam acessá-los e sua localização. Se exibir essas informações for proibido em sua organização devido aos requisitos de privacidade, você pode desabilitar o acesso ao site de controle de documento o usando o  [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) cmdlet. Você pode reabilitar o acesso ao site a qualquer momento, usando o [Enable AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037), e você pode verificar se o acesso está habilitado ou desabilitado usando atualmente [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Para executar esses cmdlets, você deve ter pelo menos a versão **2.3.0.0** do módulo RMS Azure para Windows PowerShell.  Para instruções de instalação, consulte [instalação do Windows PowerShell para Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Se você tiver baixado e instalado o módulo anteriormente, verifique o número da versão executando: `(Get-Module aadrm –ListAvailable).Version`

As seguintes URLs são usadas para controle de documentos e devem ser permitidas (por exemplo, adicioná-los aos seus Sites Confiáveis se você estiver usando o Internet Explorer com Segurança Reforçada):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Esta URL é para o Bing maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>Somente AD RMS: Suporte para vários domínios de email dentro de sua organização
Se você usa o AD RMS e usuários em sua organização tem vários domínios de email, talvez como resultado de uma fusão ou aquisição, você deve fazer a seguinte edição no registro:

1.  Navegue até **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e, se não estiver presente, crie uma nova chave chamada **RmsSharingApp**.

2.  Selecione **RmsSharingApp**, crie um novo valor de cadeia múltipla de caracteres chamado **FederatedDomains**, e adicione os domínios e todos os subdomínios que sua organização usa. Não há suporte caracteres curinga.

    Por exemplo: A empresa Coho Vineyard &amp; Winery possui um domínio de email padrão de **cohovineyardandwinery.com**, mas devido a fusões, eles também usam os domínios de email **cohowinery.com**, **eastcoast.cohowinery.com**, e **cohovineyard**. Para os dados do valor **FederatedDomains**, o administrador insere: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Se você não alterar esse registro, os usuários não poderão consumir conteúdo protegido por outros usuários em sua organização. Esta edição do registro não é necessária se você usar o Azure RMS.

## <a name="BKMK_AdminOverview"></a>Visão geral técnica do aplicativo de compartilhamento Microsoft Rights Management
O aplicativo de compartilhamento Microsoft Rights Management é um aplicativo para download opcional do Microsoft Windows e outras plataformas que oferece os seguintes recursos:

-   Proteção de um único arquivo ou em massa, proteção de vários arquivos, bem como todos os arquivos de uma pasta selecionada.

-   Suporte completo para a proteção de qualquer tipo de arquivo e um visualizador incorporado para tipos de arquivo de texto e imagem comumente usados.

-   Proteção genérica para arquivos que não dão suporte à proteção de RMS.

-   Total interoperabilidade com arquivos protegidos usando o Office Information Rights Management (IRM).

-   Total interoperabilidade com arquivos PDF protegidos usando o SharePoint, FCI e ferramentas de criação de PDF com suporte.

O aplicativo de compartilhamento Microsoft Rights Management usa o novo [AD RMS 2.1 runtime](http://www.microsoft.com/download/details.aspx?id=38396). Usando a funcionalidade do AD RMS 2.1, o aplicativo de compartilhamento Microsoft Rights Management fornece aos usuários finais uma experiência simples de proteção e de consumo.

Com o lançamento de outubro de 2013 do RMS, você pode nativamente proteger documentos usando o Office 2010 e enviá-los para pessoas de outra empresa, que pode, em seguida, consumi-los usando o Azure RMS. Além disso, com esta versão, se você usar o AD RMS em Modo Criptográfico 2, você pode usar o RMS para indivíduos e consumir conteúdo de pessoas de outra empresa que usam o Azure RMS. Para obter mais informações sobre o Modo Criptográfico 2, consulte [Modos de Criptografia do AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Níveis de proteção - nativo e genérico
Aplicativo de compartilhamento Microsoft Rights Management oferece suporte a proteção em dois níveis diferentes, conforme descrito na tabela a seguir.

|Tipo de proteção|Nativo|Genérico|
|--------------------|----------|------------|
|Descrição|Para arquivos de texto, imagem, do Microsoft Office (Word, Excel, PowerPoint), .pdf e para tipos de arquivo de outros aplicativos que suportam o AD RMS, a proteção nativa fornece um alto nível de proteção que inclui criptografia e aplicação de direitos (permissões).|Para todos os outros aplicativos e tipos de arquivo, a proteção genérica oferece um nível de proteção que inclui tanto o encapsulamento de arquivos o tipo de arquivo .pfile e autenticação para verificar se um usuário está autorizado a abrir o arquivo.|
|Proteção|Os arquivos estão completamente criptografados e a proteção é imposta das seguintes maneiras:<br /><br />-   Para que conteúdo protegido seja processado, autenticação bem-sucedida deve ocorrer para aqueles que recebem o arquivo por email ou recebem acesso a ele por meio de permissões de arquivo ou compartilhamento.<br />-   Além disso, direitos de uso e a diretiva definida pelo proprietário do conteúdo quando os arquivos são protegidos são totalmente aplicadas quando o conteúdo é renderizado no Visualizador de IP (para arquivos de texto e imagem protegidos) ou o aplicativo associado (para todos os outros tipos de arquivo com suporte).|A proteção de arquivos é imposta das seguintes maneiras:<br /><br />-   Para que conteúdo protegido seja processado, autenticação bem-sucedida deve ocorrer para aqueles que estão autorizados a abrir o arquivo e recebem acesso a ele. Se a autorização falhar, o arquivo não abre.<br />-   Direitos de uso e a diretiva definida pelo proprietário do conteúdo são exibidos para informar aos usuários autorizados a política de uso pretendido.<br />-   Log de auditoria de usuários autorizados a abrir e acessar arquivos ocorre, no entanto, sem direitos de uso são aplicados, não oferecendo suporte a aplicativos.|
|Padrão para tipos de arquivo|Isso é o nível de proteção padrão para os seguintes tipos de arquivo:<br /><br />-   Arquivos de texto e imagem<br />-   Arquivos do Microsoft Office (Word, Excel, PowerPoint)<br />-   Formato PDF (. PDF)<br /><br />Para obter mais informações, consulte a seguinte seção [Tipos de arquivo com suporte e extensões de nome de arquivo](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Isso é a proteção padrão para todos os outros tipos de arquivo (como .vsdx,. rtf e assim por diante) não tendo suporte por meio de uma proteção completa.|
Você pode alterar o nível de proteção padrão que o aplicativo de RMS sharing aplica. Você pode alterar o nível padrão de nativo para genérico, de genérico para nativo e até mesmo impedir que o aplicativo de aplicar proteção de compartilhamento do RMS. Para obter mais informações, consulte a seção [Alterando o nível de proteção padrão de arquivos](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) neste tópico.

### <a name="BKMK_SupportFileTypes"></a>Tipos de arquivo com suporte e extensões de nome de arquivo
A tabela a seguir lista os tipos de arquivos que são suportados nativamente pelo aplicativo de compartilhamento Microsoft Rights Management. Para esses tipos de arquivo, a extensão de nome de arquivo original é alterada quando a proteção nativa é aplicada, e esses arquivos se tornam somente leitura.

Além disso, quando o aplicativo RMS sharing nativamente protege um arquivo do Word, Excel ou PowerPoint cujos usuários protegem compartilhando, essa ação cria automaticamente um segundo arquivo que é uma cópia do original com o mesmo nome, mas com **.ppdf** de extensão de nome de arquivo¹. Esta versão do arquivo garante que os destinatários que instalem o aplicativo de RMS sharing sempre possam abrir o arquivo que tenha proteção nativa aplicada.

Para arquivos protegidos genericamente, a extensão de nome de arquivo original sempre é alterada para. pfile.

> [!WARNING]
> Se você tiver firewalls, proxies da web ou software de segurança que inspecione e atue de acordo com as extensões de nome de arquivo, talvez seja necessário reconfigurá-los para oferecer suporte a essas novas extensões de nome de arquivo.

|Extensão de nome de arquivo original|Extensão protegida por RMS|
|----------------------------------------|------------------------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.ppng|
|.pdf|.ppdf|
|.png|.ppng|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.jt|.pjt|
¹ Renderização de PDF fornecida pela Foxit. Copyright © 2003–2014 by Foxit Corporation.

A tabela a seguir lista os tipos de arquivo para os quais o aplicativo de compartilhamento Microsoft Rights Management oferece suporte nativo em Microsoft Office 2016, Office 2013 e Office 2010. Para esses arquivos, a extensão de nome de arquivo permanece o mesmo depois que o arquivo está protegido pelo RMS.

|Tipos de arquivo compatíveis com o Office|Tipos de arquivo compatíveis com o Office|
|---------------------------------------------|---------------------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="BKMK_ChangeDefaultProtection"></a>Alterando o nível de proteção padrão de arquivos
Você pode alterar como o aplicativo de compartilhamento RMS protege arquivos editando o registro. Por exemplo, você pode forçar os arquivos que oferecem suporte a proteção nativa a serem genericamente protegidos pelo aplicativo de RMS sharing.

Razões para que você talvez queira fazer isso.

-   Para garantir que todos os usuários possam abri-lo em seus dispositivos móveis.

-   Para garantir que todos os usuários possam abrir o arquivo que não tenha um aplicativo que oferece suporte à proteção nativa.

-   Para acomodar sistemas de segurança que atuam em arquivos por sua extensão de nome de arquivo e podem ser reconfigurados para acomodar a extensão de nome de arquivo. pfile, mas não podem ser reconfigurados para acomodar várias extensões de nome de arquivo para proteção nativa.

Igualmente, você pode forçar o aplicativo RMS sharing a aplicar a proteção nativa a arquivos como padrão, que teriam a proteção genérica aplicada. Isso pode ser apropriado se você tiver um aplicativo que oferece suporte a RMS APIs – por exemplo, um aplicativo de linha de negócios escrito por seus desenvolvedores internos ou um aplicativo comprado de um fornecedor de software independente (ISV).

Você também pode forçar o aplicativo RMS sharing a bloquear a proteção de arquivos (não aplicar proteção nativa ou proteção genérica). Por exemplo, isso pode ser necessário se você tiver um aplicativo automatizado ou serviço que deve ser capaz de abrir um arquivo específico para processar seu conteúdo. Quando você bloqueia a proteção para um tipo de arquivo, os usuários não podem usar o aplicativo de compartilhamento RMS para proteger um arquivo com esse tipo de arquivo. Quando eles tentam, eles veem uma mensagem informando que o administrador impediu a proteção e precisam cancelar suas ações para proteger o arquivo.

Para configurar o aplicativo RMS sharing a aplicar a proteção genérica a todos os arquivos como padrão, que teriam a proteção nativa aplicada, faça as seguintes edições no registro:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Crie uma nova chave chamada **&#42;**.

    Essa configuração denota arquivos com qualquer extensão de nome de arquivo.

2.  Na chave recém adicionada do **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\&#42;**, crie um novo valor de cadeia (REG_SZ) chamado **Criptografia** que possua o valor de dados de **Pfile**.

    Essa configuração resulta no aplicativo RMS sharing aplicando proteção genérica.

Essas duas configurações resultam no aplicativo RMS sharing aplicando proteção genérica para todos os arquivos que têm uma extensão de nome de arquivo. Se esse for o seu objetivo, nenhuma configuração adicional será necessária. No entanto, você pode definir exceções para tipos de arquivo específicos, para que eles ainda sejam protegidos nativamente. Para fazer isso, você deve fazer três edições adicionais do registro para cada tipo de arquivo:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Adicione uma nova chave com o nome da extensão do nome do arquivo (sem o ponto anterior).

    Por exemplo, para arquivos que têm uma extensão .docx de nome de arquivo, crie uma chave chamada **DOCX**.

2.  Na chave de tipo de arquivo recém adicionada (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), crie um novo valor DWORD chamado **AllowPFILEEncryption** que tem valor **0**.

3.  Na chave de tipo de arquivo recém adicionada (por exemplo, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), crie um novo valor de cadeia chamado **Criptografia** que tem valor **Nativo**.

Como resultado dessas configurações, todos os arquivos são genericamente protegidos exceto os arquivos que têm uma extensão de nome de arquivo. docx, que são protegidos nativamente pelo aplicativo RMS sharing.

Repita estes três passos para outros tipos de arquivos que você queira definir como exceções porque eles suportam proteção nativa e você não quer que eles sejam genericamente protegidos pelo aplicativo RMS sharing.

Você pode fazer edições de registro semelhantes para outros cenários, alterando o valor da cadeia **criptografia** que aceita os seguintes valores:

-   **Pfile**: Proteção genérica

-   **Nativo**: Proteção nativa

-   **Desativado**: Bloquear proteção

## Consulte também
[Guia do usuário do aplicativo de compartilhamento Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

