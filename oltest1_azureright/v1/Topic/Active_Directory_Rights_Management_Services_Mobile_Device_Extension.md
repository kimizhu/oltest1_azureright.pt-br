---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Extens&#227;o de dispositivos m&#243;veis do Active Directory Rights Management Services
A extensão de dispositivos móveis do AD RMS (Active Directory Rights Management Services) é executada na parte superior de uma implantação existente do AD RMS. Isso permite que os usuários que têm dispositivos móveis protejam e consumam dados confidenciais quando seu dispositivo dá suporte ao cliente RMS mais recente e usa aplicativos orientados pelo RMS. Por exemplo, os usuários nesses dispositivos podem fazer o seguinte:

-   Usar o aplicativo RMS sharing para consumo de arquivos de texto protegidos em diferentes formatos (incluindo .txt, .csv e .xml).

-   Usar o aplicativo RMS sharing para consumo de arquivos de imagem protegidos (incluindo .jpg, .gif e .tif).

-   Usar o aplicativo RMS sharing para abrir qualquer arquivo que foi protegido forma genérica (formato .pfile).

-   Usar o aplicativo RMS sharing para proteger os arquivos de imagem no dispositivo.

-   Use um visualizador de PDF orientado pelo RMS para dispositivos móveis para abrir arquivos PDF que estavam protegidos com o aplicativo RMS sharing para o Windows ou outro aplicativo orientado pelo RMS.

-   Usar outros aplicativos de fornecedores de software que oferecem aplicativos orientados pelo RMS que dão suporte a tipos de arquivo nativamente compatíveis com o RMS.

-   Usar seus aplicativos desenvolvidos internamente orientados pelo RMS que foram gravados usando o RMS SDK.

> [!NOTE]
> Você pode baixar o aplicativo de compartilhamento de RMS a partir da página [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.
> 
> Para obter mais informações sobre os diferentes tipos de arquivos aos quais o RMS oferece suporte, consulte a seção [Tipos de arquivos suportados e extensões de nome de arquivo](http://technet.microsoft.com/library/dn339003.aspx) no guia do administrador do aplicativo de compartilhamento do Rights Management.

Você não precisa da extensão de dispositivos móveis para consumir ou escrever email protegido em dispositivos se eles usarem aplicativos de email que dão suporte ao IRM do Exchange ActiveSync. Esse suporte nativo para o RMS e dispositivos móveis foi introduzido com o Exchange 2010 Service Pack 1.

Use as seções a seguir para implantar a extensão de dispositivos móveis do AD RMS (Active Directory Rights Management Services):

-   [Pré-requisitos para a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Configurando o AD FS para a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Configurando o AD FS para a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Especificando os registros do SRV de DNS para a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Implantando a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Pré-requisitos para a extensão de dispositivos móveis do AD RMS
Antes de instalar a extensão de dispositivos móveis do AD RMS, verifique se estas dependências estão no local.

|Requisito|Mais informações|
|-------------|--------------------|
|Uma implantação do AD RMS existente no Windows Server 2012 R2 ou no Windows Server 2012. **Note:** O AD RMS deve estar usando um banco de dados completo baseado no Microsoft SQL Server em um servidor separado, e não o banco de dados interno do Windows que muitas vezes é usado para teste no mesmo servidor.|Para obter a documentação sobre o AD RMS, consulte [Serviços do Rights Management no Active Directory](http://technet.microsoft.com/library/hh831364.aspx) na biblioteca do Windows Server.|
|AD FS implantado no Windows Server 2012 R2|Para obter a documentação sobre ADFS, consulte o [Guia de implementação do Windows Server 2012 R2 AD FS](http://technet.microsoft.com/library/dn486820.aspx) na biblioteca do Windows Server.<br /><br />O AD FS deve ser configurado para a extensão de dispositivos móveis. Para obter instruções, consulte a seção [Configurando o AD FS para a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) nesse tópico.|
|Registros do SRV no DNS|Crie um ou mais registros do SRV no domínio ou domínios em sua empresa:<br /><br />-   Um registro para cada sufixo de domínio de email que os usuários usarão<br />-   Um registro para cada FQDN usado pelo seus clusters RMS para proteger o conteúdo<br /><br />Quando os usuários fornecem seus endereços de email de seus dispositivos móveis, o sufixo de domínio é usado para identificar se eles devem usar uma infraestrutura do AD RMS ou do Azure RMS. Quando o registro de SRV for encontrado, os clientes serão redirecionados ao servidor do AD RMS que responda a esta URL.<br /><br />Quando os usuários consomem conteúdo protegido com um dispositivo móvel, o aplicativo cliente procura no DNS um registro que corresponde ao FQDN na URL do cluster que protegeu o conteúdo. O dispositivo, em seguida, é direcionado ao cluster AD RMS especificado no registro de DNS e obtém uma licença para abrir o conteúdo. Na maioria dos casos, o cluster RMS será o mesmo cluster RMS que protegeu o conteúdo.<br /><br />Para obter informações sobre como especificar os registros SRV, consulte a seção [Especificando os registros do SRV de DNS para a extensão de dispositivos móveis do AD RMS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) nesse tópico.|
|Clientes com suporte atualmente:<br /><br />-   Dispositivos Android usando a versão mais recente do aplicativo RMS sharing para Android|Versão mínima do Android 4.0.3.<br /><br />Baixe o aplicativo de compartilhamento RMS para o Android a partir do [site Microsoft Connect](https://connect.microsoft.com/site1170/Downloads) e faça o sideload dele para o dispositivo.|

### <a name="BKMK_ADFS"></a>Configurando o AD FS para a extensão de dispositivos móveis do AD RMS
Você deve configurar o AD FS e, em seguida, autorizar o aplicativo RMS sharing para Android.

##### Etapa 1: Para configurar o AD FS

-   Você pode executar um script do Windows PowerShell para configurar automaticamente o AD FS para dar suporte à extensão de dispositivos móveis do AD RMS ou pode especificar manualmente as opções de configuração e os valores:

    -   Para configurar automaticamente o AD FS, copie e cole o seguinte em um arquivo de script do Windows PowerShell e, em seguida, execute-o:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Para configurar manualmente o AD FS, use estas configurações:

        |Configuração|Valor|
        |----------------|---------|
        |**Objeto de confiança de terceira parte confiável**|api.rms.rest.com|
        |**Regra de declaração**|**Repositório de atributos**:  Active Directory<br /><br />**Endereços de email**:  Endereço de email<br /><br />**Nome UPN**:  UPN<br /><br />**Endereço proxy**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Etapa 2: Autorizar o aplicativo RMS sharing para Android

-   Execute o seguinte comando do Windows PowerShell para adicionar suporte para dispositivos Android:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>Especificando os registros do SRV de DNS para a extensão de dispositivos móveis do AD RMS
Você deve criar registros do SRV de DNS para cada domínio de email que seus usuários usam. Se todos os seus usuários usarem domínios filho de um domínio pai único e todos os usuários deste namespace contíguo de usarem o mesmo cluster RMS, você poderá usar apenas um registro de SRV no domínio pai, e o RMS encontrará os registros DNS apropriados.

Os registros de SRV têm o seguinte formato: _rmsdisco._http._tcp. *&lt;emailsuffix&gt;**&lt;portnumber&gt;**&lt;RMSClusterFQDN&gt;*

Por exemplo, se sua organização tiver usuários com os endereços de email a seguir:

-   usario@contoso.com

-   usuario@sales.contoso.com

-   usuario@fabrikam.com

- e não existem outros domínios filho para contoso.com que usem um cluster RMS diferente do que o chamado **rmsserver.contoso.com**, crie dois registros do servidor DNS que tenham os seguintes valores:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Além desses registros do SRV de DNS para os domínios de email, você deve criar outro registro do SRV de DNS nos domínios de usuário. Esse registro deve especificar as URLs do cluster RMS que protege o conteúdo. Todos os arquivos protegidos pelo RMS incluem uma URL para o cluster que protegeu esse arquivo. Dispositivos móveis usam o registro do SRV de DNS e o FQDN da URL especificada no registro para encontrar o cluster RMS correspondente que pode dar suporte a dispositivos móveis.

Por exemplo, se o cluster RMS for **rmsserver.contoso.com**, crie um registro SRV DNS que tenha os seguintes valores: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Implantando a extensão de dispositivos móveis do AD RMS
Antes de instalar a extensão de dispositivos móveis do AD RMS, verifique se os pré-requisitos da seção precedente estão no local e se você sabe a URL do servidor AD FS. Em seguida, faça o seguinte:

1.  Baixe a extensão do dispositivo móvel AD RMS a partir do [site do Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Execute Setup.exe para iniciar o Assistente de instalação da extensão de dispositivos móveis do Active Directory Rights Management Services.

3.  Quando solicitado, insira a URL do servidor AD FS que você configurou anteriormente.

4.  Conclua o assistente.

Execute este assistente em todos os nós no cluster RMS.

