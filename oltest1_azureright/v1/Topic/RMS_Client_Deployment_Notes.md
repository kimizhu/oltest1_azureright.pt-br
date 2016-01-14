---
description: na
keywords: na
title: RMS Client Deployment Notes
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
---
# Observa&#231;&#245;es de Implanta&#231;&#227;o do Cliente RMS
A versão do Rights Management Services client (cliente RMS) 2 também é conhecida como o cliente MSIPC. É o software para computadores com Windows que se comunica com os serviços do Microsoft Rights Management localmente ou na nuvem para ajudar a proteger o acesso e o uso de informações conforme ela flui através de aplicativos e dispositivos, dentro dos limites da sua organização ou fora de tais limites gerenciados. Além de envio com o [compartilhamento de aplicativos para Windows Rights Management](https://technet.microsoft.com/library/dn919648.aspx), o cliente RMS está disponível [como um download opcional](http://www.microsoft.com/download/details.aspx?id=38396) que pode, com o reconhecimento e aceitação de seu contrato de licença, ser distribuído gratuitamente com o software de terceiros para que os clientes possam proteger e consumir conteúdo protegido pelos serviços de gerenciamento de direitos.

Este tópico inclui as seções a seguir:

-   [Redistribuindo o cliente RMS](#BKMK_RedistributeInstaller)

-   [Instalando o cliente RMS](#BKMK_InstallClient)

-   [Perguntas e respostas sobre o cliente RMS](#BKMK_QA)

-   [Configurações do cliente RMS](#BKMK_Settings)

-   [Somente AD RMS: Limitar o cliente RMS para usar servidores de AD RMS confiáveis](#BKMK_UsingTrustedServers)

-   [Descoberta de serviço RMS](#BKMK_ServiceDiscovery)

## <a name="BKMK_RedistributeInstaller"></a>Redistribuindo o cliente RMS
O cliente RMS pode ser redistribuído livremente e agrupado com outros aplicativos e soluções de TI. Se você for um desenvolvedor de aplicativos ou um provedor de soluções e quer redistribuir o cliente RMS, você tem duas opções:

-   Recomendado: Incorporar o instalador do cliente RMS na instalação do aplicativo e executá-lo no modo silencioso (o **/quiet** switch, detalhado na próxima seção).

-   Tornar o cliente RMS um pré-requisito para o seu aplicativo. Com essa opção, você precisará fornecer aos usuários instruções adicionais para que eles possam obter, instalar e atualizar os seus computadores com o cliente antes de usar o seu aplicativo.

## <a name="BKMK_InstallClient"></a>Instalando o cliente RMS
O cliente RMS está contido em um arquivo executável do instalador chamado **setup_msipc_***&lt; arch &gt;***.exe**, onde *&lt; arch &gt;* é **x86** (para computadores cliente de 32 bits) ou **x64** (para computadores cliente de 64 bits). O pacote de instalação de 64 bits (x64) instala tanto um executável de 32 bits para compatibilidade com aplicativos de 32 bits que são executados em uma instalação de sistema operacional de 64 bits, como um executável de 64 bits para dar suporte a aplicativos de 64 bits nativos. O instalador de 32 bits (x86) não será executado em uma instalação do Windows de 64 bits.

> [!NOTE]
> Você precisa de privilégios elevados para instalar o cliente RMS, como um membro do grupo Administradores no computador local.

Você pode instalar o cliente RMS usando qualquer um dos seguintes métodos de instalação:

-   **Modo silencioso.** Usando o **/quiet** switch como parte das opções de linha de comando, você pode instalar silenciosamente o cliente RMS nos computadores. O seguinte exemplo mostra uma instalação no modo silencioso para o cliente RMS em um computador cliente de 64 bits:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Modo interativo.** Como alternativa, você pode instalar o cliente RMS usando o programa de instalação baseada em GUI que é fornecido pelo Assistente de instalação do cliente RMS. Para o fazer, clique duas vezes no pacote de instalação do cliente RMS (**setup_msipc_***&lt; arch &gt;***.exe**) na pasta para a qual ele foi copiado ou baixado em seu computador local.

## <a name="BKMK_QA"></a>Perguntas e respostas sobre o cliente RMS
A seguinte seção contém perguntas frequentes sobre o cliente RMS e as respectivas respostas.

### Quais sistemas operacionais oferecem suporte para o cliente RMS?
O cliente RMS é compatível com os seguintes sistemas operacionais:

|Sistema Operacional Windows Server|Sistema Operacional Cliente Windows|
|--------------------------------------|---------------------------------------|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 com pelo menos SP1|
|Windows Server 2008 (somente AD RMS)|Windows Vista com pelo menos SP2 (somente AD RMS)|

### Quais processadores ou plataformas suportam o cliente RMS?
O cliente RMS é suportado em computadores com plataformas de computação x86 e x64.

### Onde o cliente RMS está instalado?
Por padrão, o cliente RMS é instalado em %ProgramFiles%\Active Directory Rights Management Services Client 2. &lt; número de versão secundária &gt;.

### Quais arquivos estão associados ao software cliente RMS?
Os seguintes arquivos são instalados como parte do software cliente RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Além desses arquivos, o cliente RMS também instala arquivos de suporte de interface do usuário multilíngue (MUI) em 44 idiomas. Para verificar os idiomas com suporte, execute a instalação do cliente RMS e quando a instalação for concluída, examine o conteúdo das pastas de suporte multilíngue no caminho padrão.

### O cliente RMS é incluído por padrão ao instalar um sistema operacional?
Não. Esta versão do cliente RMS é fornecida como um download opcional que pode ser instalado separadamente em computadores que executam versões do sistema operacional Microsoft Windows suportadas.

### O cliente RMS é atualizado automaticamente pelo Microsoft Update?
Se instalou o cliente RMS usando a opção de instalação silenciosa, o cliente RMS herda as suas definições atuais do Microsoft Update, Se instalou o cliente RMS usando a opção de instalação silenciosa, o programa de instalação do cliente RMS lhe pede para ativar o Microsoft Update.

## <a name="BKMK_Settings"></a>Configurações do cliente RMS
A seguinte seção contém informações de configuração sobre o cliente RMS. Essas informações podem ser úteis se você tiver problemas com aplicativos ou serviços que usam o cliente RMS.

> [!NOTE]
> Algumas configurações dependem se o aplicativo aprimorados pelo RMS é executado como um aplicativo de modo de cliente (como Microsoft Word e Outlook ou o aplicativo de compartilhamento RMS) ou o aplicativo de modo de servidor (por exemplo, SharePoint e Exchange).  Nas seguintes tabelas, tais configurações são identificadas como **modo cliente** e **modo de servidor**, respectivamente.

### Onde o cliente RMS armazena as licenças nos computadores cliente
O cliente RMS armazena licenças no disco local e também armazena algumas informações no registro do Windows.

|Descrição|Caminhos de modo cliente|Caminhos de modo servidor|
|-------------|----------------------------|-----------------------------|
|Local de armazenamento de licenças|%localappdata%\Microsoft\MSIPC|%allusersprofile%\Microsoft\MSIPC\Server\*&lt;SID&gt;*\|
|Local de armazenamento de modelos|%localappdata%\Microsoft\MSIPC\Templates|%allusersprofile%\Microsoft\MSIPC\Server\Templates\*&lt;SID&gt;*\|
|Local do registro|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Configurações Locais<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*&lt;SID&gt;*|
> [!NOTE]
> *&lt; SID &gt;* é o identificador de seguro (SID) para a conta sob a qual o aplicativo de servidor está em execução. Por exemplo, se o aplicativo é executado sob a conta de serviço de rede interna, substitua *&lt; SID &gt;* com o valor do SID bem conhecido para tal conta (S-1-5-20).

### Configurações de registro do Windows para o cliente RMS
Você pode usar as chaves de registro do Windows para definir ou modificar algumas configurações do cliente RMS. Por exemplo, como um administrador de aplicativos aprimorados pelo RMS que se comunicam com servidores AD RMS, convém atualizar o local do serviço corporativo (substituição do servidor AD RMS que no momento está selecionado para publicação) dependendo da localização atual do computador cliente dentro de sua topologia do Active Directory. Ou, talvez você queira habilitar o rastreamento do RMS no computador cliente, para ajudar a solucionar um problema com um aplicativo aprimorado pelo RMS. Use a seguinte tabela para identificar as configurações do registro que podem ser alteradas para o cliente RMS.

|Tarefa|Configurações|
|----------|-----------------|
|Somente AD RMS: Para atualizar o local do serviço de empresa para um computador cliente|Atualize as seguintes chaves de registro:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />    REG_SZ: padrão<br />    **Value:**&lt;http or https&gt;:// *RMS_Cluster_Name*/_wmcs/Certification<br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />    REG_SZ: default<br />    **Value:** &lt;http or https&gt;:// *RMS_Cluster_Name*/_wmcs/Licensing|
|Para ativar e desativar o rastreamento|Atualize as seguintes chaves de registro:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />    REG_DWORD: Rastreamento<br />    **Valor:** 1 para ativar o rastreamento, 0 para desativar o rastreamento (padrão)|
|Para alterar a frequência em dias de atualização dos modelos|Os seguintes valores do registro especificam com que frequência os modelos serão atualizados no computador do usuário se o valor de TemplateUpdateFrequencyInSeconds não está definido.  Se nenhum desses valores estiverem definidos, o intervalo padrão de atualização para aplicativos que usam o cliente RMS (versão 1.0.1784.0) para fazer o download de modelos é 1 dia. Versões anteriores têm um valor padrão de cada 7 dias.<br /><br />**Modo Cliente:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Valor:** Um valor inteiro que especifica o número de dias (mínimo de 1) entre downloads.<br /><br />**Modo Servidor:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt;SID&gt;*<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Valor:** Um valor inteiro que especifica o número de dias (mínimo de 1) entre downloads.|
|Para alterar a frequência em segundos de atualização dos modelos **Important:** Se for especificado, o valor para atualizar os modelos em dias será ignorado. Especifique um ou o outro, não ambos.|Os seguintes valores do registro especificam com que frequência os modelos serão atualizados no computador do usuário. Se esse valor ou o valor para alterar a frequência em dias (TemplateUpdateFrequency) não estiver definido, o intervalo padrão de atualização para aplicativos que usam o cliente RMS (versão 1.0.1784.0) para fazer o download de modelos é 1 dia. Versões anteriores têm um valor padrão de cada 7 dias.<br /><br />**Modo Cliente:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Valor:** Um valor inteiro que especifica o número de segundos (mínimo de 1) entre downloads.<br /><br />**Modo Servidor:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt;SID&gt;*<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Valor:** Um valor inteiro que especifica o número de segundos (mínimo de 1) entre downloads.|
|Somente AD RMS: Para baixar modelos imediatamente na próxima solicitação de publicação|Durante testes e avaliações, poderá querer que o cliente RMS baixe modelos assim que possível. Para o fazer, remova a seguinte chave do registro e o cliente RMS irá baixar modelos imediatamente na próxima solicitação de publicação em vez de aguardar o tempo especificado pela configuração do registro TemplateUpdateFrequency:<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\&lt;Server Name&gt;\Template **Note:** &lt; nome do servidor &gt; poderia ter URLs externo (corprights.contoso.com) e interno (corprights) e, portanto, duas entradas diferentes.|
|Somente AD RMS: Para habilitar o suporte para autenticação federada|Se o computador cliente RMS se conecta a um cluster AD RMS por meio de uma confiança federada, você deve configurar o realm (casa) inicial da federação.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_SZ: FederationHomeRealm<br />    **Valor:** O valor desta entrada do registro é o uniform resource identifier (URI) do serviço de Federação (por exemplo, "https://fs-01.contoso.com").|
|Somente AD RMS: Para dar suporte a servidores de Federação parceiros que exigem a autenticação baseada em formulários de entrada do usuário|Por padrão, o cliente RMS opera no modo silencioso e entrada do usuário não é necessária. No entanto, Servidores de Federação Parceiros podem ser configurados para exigir a entrada do usuário através da autenticação baseada em formulários. Nesse caso, você deve configurar o cliente RMS para ignorar o modo silencioso para que o formulário de autenticação federada seja exibido em uma janela do navegador e o usuário é promovido para autenticação.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_DWORD: EnableBrowser **Note:** Se o servidor de Federação está configurado para usar a autenticação baseada em formulários, essa chave é necessária. Se o servidor de Federação está configurado para usar a autenticação integrada do Windows, essa chave é necessária.|
|Somente AD RMS: Para bloquear o consumo do serviço ILS|Por padrão, o cliente RMS permite consumir conteúdo protegido pelo serviço ILS, mas você pode configurar o cliente para bloquear tal serviço, definindo a seguinte chave do registro. Se essa chave do registro for definida para bloquear o serviço ILS, qualquer tentativa de abrir e consumir conteúdo protegido pelo serviço ILS retornará o seguinte erro:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: **DisablePassportCertification**<br />    **Valor:** 1 para bloquear o consumo ILS, 0 para permitir o consumo ILS (padrão)|

### Gerenciar a distribuição de modelos para o cliente RMS
Modelos facilitam para os usuários e administradores a aplicação rápida da proteção do Rights Management e o cliente RMS baixa automaticamente modelos de seus servidores RMS ou serviço se você colocar os modelos no seguinte local de pasta, o cliente RMS não baixará os modelos de seu local padrão e em vez disso, baixa os modelos que você colocou nessa pasta. O cliente RMS pode continuar a baixar modelos de outros servidores RMS disponíveis.

**Modo cliente:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Modo de servidor:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*&lt; SID &gt;*

Quando você usa essa pasta, não há nenhum convenção de nomenclatura especial necessária exceto que os modelos devem ser emitidos pelo servidor ou serviço RMS e devem ter a extensão de nome de arquivo .xml. Por exemplo, Contoso-Confidential.xml ou Contoso-ReadOnly.xml são nomes válidos.

## <a name="BKMK_UsingTrustedServers"></a>Somente AD RMS: Limitar o cliente RMS para usar servidores de AD RMS confiáveis
O cliente RMS pode ser limitado ao uso de somente servidores AD RMS específicos e confiáveis fazendo as seguintes alterações no registro do Windows em computadores locais.

**Para limitar o cliente RMS para usar somente servidores de AD RMS confiáveis**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Valor:** Se for especificado um valor diferente de zero, o cliente RMS confiará somente nos servidores especificados que estão configurados na lista TrustedServers e no serviço de gerenciamento de direitos do Azure.

**Para adicionar membros à lista de servidores confiáveis do AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *&lt;URL_or_HostName&gt;*

    **Valor:** Os valores de cadeia de caracteres adicionados neste local de chave do Registro podem ser um dos formatos de nome de domínio DNS (por exemplo, **adrms.contoso.com**) ou URLs completos de servidores confiáveis do AD RMS (por exemplo, **https://adrms.contoso.com**). Se uma URL especificada começa com **https://**,  o cliente RMS usará SSL ou TLS para entrar em contato com o servidor de AD RMS especificado.

## <a name="BKMK_ServiceDiscovery"></a>Descoberta de serviço RMS
A descoberta de serviço RMS permite que o cliente RMS verifique com qual servidor ou serviço RMS deve se comunicar antes de proteger o conteúdo. Descoberta de serviço também pode acontecer quando o cliente RMS consumir conteúdo protegido, mas isso tem menos probabilidade de acontecer porque a diretiva anexada ao conteúdo contém o servidor ou serviço RMS preferencial e somente se for malsucedida o cliente, em seguida, executa descoberta de serviço.

A descoberta do serviço primeiro procura por uma versão local do Rights Management (AD RMS). Se não for bem-sucedida, a descoberta de serviço procura automaticamente a versão de nuvem do Rights Management (Azure RMS).

Para executar a descoberta de serviço para a implantação no local, o cliente RMS verifica o seguinte:

1.  O registro do Windows no computador local: Se as configurações de descoberta de serviço são configuradas no registro, essas configurações terão prioridade.  Por padrão, essas configurações não são configuradas no registro.

2.  Serviços de Active Directory Domain: Um computador de domínio consulta o Active Directory para um ponto de conexão de serviço (SCP). Se um SCP estiver registrado, a URL do servidor RMS é retornada para o cliente RMS usar.

### Somente AD RMS: Habilitação da descoberta do serviço do lado do servidor por meio do Active Directory
Se sua conta tiver privilégios suficientes (administradores de empresa e administrador local para o servidor de AD RMS), você pode registrar automaticamente um ponto de conexão de serviço (SCP) quando você instala o servidor de cluster raiz AD RMS. Se já existir um SCP na floresta, exclua primeiro o SCP existente antes de registrar um novo.

Você pode registrar e excluir um SCP após a instalação do AD RMS usando o seguinte procedimento. Antes de começar, certifique-se de que sua conta tem os privilégios necessários (administradores de empresa e administrador local para o servidor de AD RMS).

##### Para habilitar a descoberta de serviço AD RMS registrando um SCP no Active Directory

1.  Abra o console de serviços de gerenciamento do Active Directory no servidor AD RMS:

    -   Se você estiver usando o Windows Server 2008 R2 ou o Windows Server 2008, clique em **Iniciar**, clique em **Ferramentas administrativas**, e, em seguida, clique em **Active Directory Rights Management Services**.

    -   Se você estiver usando o Windows Server 2012 R2 ou o Windows Server 2012, clique em **Ferramentas**, e, em seguida, clique em **Active Directory Rights Management Services**.

2.  No console do AD RMS clique com o botão direito do cluster AD RMS e, em seguida, clique em **Propriedades**.

3.  Clique na guia **SCP**.

4.  Selecione **Alterar SCP** na caixa de seleção.

5.  Selecione **Definir SCP para o atual cluster de certificação** e, em seguida, clique em **OK**.

### Habilitação da descoberta de serviço do lado do cliente usando o registro do Windows
Como alternativa ao uso de um SCP ou onde um SCP não existir, você pode configurar o registro no computador cliente para que o cliente RMS possa localizar o servidor de AD RMS.

##### Para permitir a descoberta de serviço AD RMS do lado do cliente usando o registro do Windows

1.  Abra o editor de registro do Windows, Regedit.exe:

    -   No computador cliente, na janela Executar, digite **regedit**, e pressione ENTER para abrir o Editor do registro.

2.  No Editor do registro, navegue até **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Se você estiver executando um aplicativo de 32 bits em um computador de 64 bits, o caminho será o seguinte: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  Para criar a subchave ServiceLocation, clique com o botão direito em **MSIPC**, aponte para **Novo**, clique em **chave**, e digite **ServiceLocation**.

4.  Para criar a subchave EnterpriseCertification, clique com botão direito em **ServiceLocation**, aponte para **Novo**, clique em **Chave**, e digite **EnterpriseCertification**.

5.  Para definir a URL de certificação corporativa, clique duas vezes no valor **(Padrão)** na subchave **EnterpriseCertification** e quando a caixa de diálogo **Editar cadeia de caracteres** aparecer, para **dados do valor**, digite &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Certification e, em seguida, clique em **OK**.

6.  Para criar a subchave EnterprisePublishing, clique com o botão direito em **ServiceLocation**, aponte para **Novo**, clique em **Chave**, e digite EnterprisePublishing.

7.  Para definir a URL de certificação de publicação, clique duas vezes em **(Padrão)** na subchave **EnterprisePublishing** e quando a caixa de diálogo **Editar cadeia de caracteres** aparecer, para **dados do valor**, digite o seguinte &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Licensing e então clique em **OK**.

8.  Feche o editor do registro.

Se o cliente RMS não consegue localizar um SCP consultando o Active Directory e não for especificado no registro, chamadas de descoberta de serviço do AD RMS falharão.

### Redirecionando o tráfego do servidor de licenciamento
Em alguns casos, talvez seja necessário redirecionar tráfego durante a descoberta de serviço, por exemplo, quando duas organizações são mescladas e o servidor de licenciamento antigo em uma organização está desativado e os clientes precisam ser redirecionados para um novo servidor de licenciamento. Ou, quando migrar de um AD RMS para um Azure RMS. Para habilitar o redirecionamento de licenciamento, use o seguinte procedimento.

##### Para habilitar o redirecionamento de licenciamento RMS usando o registro do Windows.

1.  Abra o editor de registro do Windows, Regedit.exe:

    -   No computador cliente, na janela Executar, digite **regedit**, e pressione ENTER para abrir o Editor do registro.

2.  No Editor do registro, navegue até um dos seguintes:

    -   Para versões de 64 bits do Office em plataforma x64: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Para versões de 32 bits do Office em plataforma x64: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Crie uma subchave LicensingRedirection, clicando com o botão direito em **Servicelocation**, aponte para **Novo**, clique em **Chave**, e digite **LicensingRedirection**.

4.  Para configurar o redirecionamento de licenciamento, clique com o botão direito na subchave **LicensingRedirection**, selecione **Novo**, e, em seguida, selecione **valor de cadeia de caracteres**.  Para **Nome**, especifique o URL de licenciamento de servidor anterior e para **Valor** especifique o novo URL do servidor de licenciamento.

    Por exemplo, para redirecionar o licenciamento de um servidor em Contoso.com para Fabrikam.com, você pode inserir os seguintes valores:

    **Name:** `https://contoso.com/_wmcs/licensing`

    **Value:** `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Se o servidor de licenciamento antigo tiver URLs de extranet e de intranet especificadas, então, um novo nome e mapeamento de valor precisa ser definido para ambas as URLs na chave LicensingRedirection.

5.  Repita a etapa anterior para todos os servidores que precisam ser redirecionados.

6.  Feche o editor do registro.

