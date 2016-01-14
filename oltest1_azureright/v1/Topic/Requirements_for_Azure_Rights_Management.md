---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Requisitos para o Azure Rights Management
Para implantar o Microsoft Azure Rights Management (Azure RMS) em sua organização, certifique-se de ter os seguintes pré-requisitos. Você pode, em seguida, usar o [Roteiro de implantação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para implantar o Rights Management na sua organização.

|Requisito|Mais informações|
|-------------|--------------------|
|Uma assinatura de nuvem para o RMS|Sua organização deve ter uma assinatura de nuvem que ofereça suporte ao RMS.<br /><br />Para obter informações sobre licenciamento, consulte a seção [Assinaturas de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)neste tópico.|
|Diretório do AD do Azure|Sua organização deve ter um diretório do AD do Azure para oferecer suporte à autenticação de usuário para o RMS. Além disso, se você quiser usar as contas de usuário do seu diretório local (AD DS), também será necessário configurar a integração do diretório.<br /><br />O Multi-Factor Authentication (MFA) é compatível com o Azure RMS quando você tem o software cliente necessário e a infraestrutura de suporte do MFA configurada corretamente.<br /><br />Para obter mais informações, consulte a seção [Diretório do AD do Azure](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) neste tópico.|
|Dispositivos cliente|Os usuários devem ter um dispositivo cliente (computador ou dispositivo móvel) que execute um sistema operacional que suporte o RMS.<br /><br />Para obter mais informações, consulte a seção [Dispositivos cliente que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) neste tópico.|
|Aplicativos|Os usuários devem executar aplicativos que suportem o RMS.<br /><br />Para obter mais informações, consulte a seção [Aplicativos que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) neste tópico.|
|Infraestrutura que oferece suporte à conectividade com a Internet e serviços em nuvem dependentes|Se você tiver um firewall ou dispositivos de interrupção de rede semelhantes que devem ser configurados para permitir conexões específicas, consulte os [intervalos de endereços IP e URLs do Office 356](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />A lista de URLs e de endereços IP na seção **portal do Office 356 e identidade** são aplicadas para o portal do Office 365, recursos do Active Directory do Azure e Azure Rights Management. Use as instruções neste artigo para se manter atualizado em relação às alterações dessas informações, inscrevendo-se em um RSS feed.<br /><br />Além das informações no artigo do Office, há outras especificações para o Azure RMS:<br /><br />-   Não encerrar a conexão de serviço do cliente TLS (por exemplo, fazer inspeção no nível de pacote). Isso interrompe a fixação de certificado que os clientes RMS usam com CAs gerenciados pela Microsoft para ajudar a proteger suas comunicações com o Azure RMS.<br />-   Não use uma configuração de proxy da Web que autentique em nome de um usuário.|

Se quiser usar o Azure RMS com servidores locais, os seguintes produtos são compatíveis:

-   Exchange Server

-   SharePoint Server

-   Servidores de arquivos Windows Server que suportem FCI (Infraestrutura de Classificação de Arquivos)

Para obter informações sobre os requisitos adicionais do Azure RMS para este cenário, consulte a seção [Servidores no local que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers)neste tópico.

> [!IMPORTANT]
> Não há suporte para o cenário de implantação a seguir:
> 
> -   Executando o AD RMS e o Azure RMS lado a lado na mesma organização, exceto durante migrações, conforme descrito em [Migrando do AD RMS para o Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> Há um caminho de migração com suporte [do AD RMS para o Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx) e do [Azure RMS para AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Se você implantar o Azure RMS e, em seguida, decidir que não deseja usar esse serviço de nuvem, consulte [Encerramento e desativação do Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Use as seções a seguir para saber mais sobre os requisitos do Azure RMS.

## <a name="BKMK_SupportedSubscriptions"></a>Assinaturas de nuvem que suportam o Azure RMS
Para usar o Azure RMS, sua organização deve ter pelo menos uma das seguintes assinaturas com um número suficiente de licenças para usuários e serviços que protegem arquivos e mensagens de email. Se você tiver um serviço que aplique a proteção para os usuários (os proprietários dos arquivos ou mensagens de email), os usuários precisam de uma dessas licenças. Os usuários que só irão consumir (por exemplo, ler e editar) esses dados protegidos não precisam de uma licença.

-   Office 365

-   Azure Rights Management Premium (anteriormente Azure RMS Standalone)

-   Enterprise Mobility Suite

-   RMS para pessoas físicas

Use as seções a seguir para obter mais informações e opções de inscrição.

Para obter uma comparação dos recursos do Azure RMS para as assinaturas pagas de licenciamento, consulte [Comparação dos Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

### Assinatura do Office 365
[Avaliação gratuita de 30 dias: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Esta assinatura foi desenvolvida para organizações que desejam utilizar os serviços online do Office e usar o recurso Information Rights Management, que usa o Azure RMS. No entanto, nem todas as assinaturas do Office 365 incluem o Azure RMS.

|Opção de licenciamento|Conceitos básicos do Office 365 Business|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|--------------------------|--------------------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Information Rights Protection (IRM)|Não|Não|Não|Sim|Sim|Sim|Não|Não|Não|

### Assinatura do Azure Rights Management Premium
[Avaliação gratuita de 30 dias](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Esta assinatura era conhecida anteriormente como Azure RMS Standalone e foi projetada para organizações que desejam usar o Azure RMS, mas que ainda não possuem uma assinatura que inclua o Azure RMS. Por exemplo, se tiver uma assinatura do Office 365 Business Essentials ou Office 365 Enterprise E1, essas assinaturas não incluem o Azure RMS (consulte a tabela na seção anterior). Para usar o Azure RMS, você poderia comprar uma assinatura do Azure Rights Management Premium (ou comprar outra assinatura, como o Office 365 Enterprise E4 que inclui o Azure RMS).

Para obter mais informações, consulte [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Esta assinatura também oferece um período de avaliação para experimentar o Azure RMS para 25 usuários, sem custo. Se a assinatura expira antes que você compre uma assinatura de substituição, consulte a seção seguinte, "O quê acontece quando a assinatura de avaliação expira?"

|Opção de licenciamento|Conceitos básicos do Office 365 Business|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|--------------------------|--------------------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Information Rights Protection (IRM)|Sim|Sim <sup>1</sup>|Sim|Sim|Sim|Sim|Sim|Sim|Sim|
<sup>1</sup> For Business Premium, há algumas restrições de cliente: Você pode proteger o conteúdo e consumir conteúdo protegido com o RMS usando o Outlook Web App e o aplicativo de compartilhamento do RMS. Você pode consumir o conteúdo protegido usando todos os outros aplicativos do Office, o que inclui o Office Online e os aplicativos cliente do Office 365 Business Premium.

#### <a name="BKMK_TrialExpiryBehavior"></a>O quê acontece quando a assinatura de avaliação expira?
Se sua assinatura de avaliação expira, você perderá acesso ao conteúdo que foi protegido usando sua assinatura de avaliação para o Azure RMS. No entanto, se você compra uma assinatura que ofereça suporte ao Azure RMS, o acesso é automaticamente restaurado.

Uma exceção para perder o acesso após a expiração é se a sua organização usou o Azure RMS com o RMS para assinaturas individuais antes que você obtenha a assinatura de avaliação. Depois, o acesso à conteúdo anteriormente protegido permanece, mesmo depois que a assinatura de avaliação expira.

### Assinatura do Enterprise Mobility Suite
[Avaliação gratuita de 30 dias](http://go.microsoft.com/fwlink/?LinkId=615385)

Esta assinatura foi desenvolvida para organizações que querem usar uma combinação do Azure Active Directory Premium, do Windows Intune e do Azure Rights Management. Para obter mais informações, consulte a [Visão Geral do Microsoft Enterprise Mobility](http://go.microsoft.com/fwlink/?LinkId=615386).

|Opção de licenciamento|Conceitos básicos do Office 365 Business|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Plan 1<br />SharePoint Plan 2|Exchange Online Plan 1<br />Exchange Online Plan 2|
|--------------------------|--------------------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|Information Rights Protection (IRM)|Sim|Sim <sup>1</sup>|Sim|Sim|Sim|Sim|Sim|Sim|Sim|
<sup>1</sup> For Business Premium, há algumas restrições de cliente: Você pode proteger o conteúdo e consumir conteúdo protegido com o RMS usando o Outlook Web App e o aplicativo de compartilhamento do RMS. Você pode consumir o conteúdo protegido usando todos os outros aplicativos do Office, o que inclui o Office Online e os aplicativos cliente do Office 365 Business Premium.

### Assinatura do RMS para indivíduos
Esta assinatura foi desenvolvida para indivíduos de uma organização que não implantou o Azure RMS ou o AD RMS. Ela permite que essas pessoas leiam conteúdo protegido por uma organização que use o Azure RMS, e também podem proteger seus próprios conteúdos.

Para obter mais informações, consulte [RMS para pessoas físicas e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Diretório do AD do Azure
É necessário ter um diretório do AD do Azure para usar o Azure RMS. Você pode usar a conta da sua organização deste diretório para acessar o Portal clássico do Azure, onde, por exemplo, é possível configurar e gerenciar modelos do Rights Management.

Se você ainda não tiver uma assinatura do Azure para sua organização, obtenha uma assinando uma versão gratuita. Vá para a página de [Introdução ao Azure](https://account.windowsazure.com/organization) e siga as instruções.

Para obter mais informações, consulte os seguintes recursos na documentação do Azure Active Directory:

-   [O que é um diretório do AD do Azure?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Como as assinaturas do Azure estão associadas ao AD do Azure](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Se deseja integrar seu diretório do AD do Azure com as florestas do AD local, consulte [Integração de diretórios](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Se você possui dispositivos móveis ou computadores Mac que autenticam no local usando AD FS ou um provedor de autenticação equivalente:
> 
> -   Você deve usar AD FS na versão mínima do servidor de **Windows Server 2012 R2**, ou um provedor de autenticação alternativo compatível com o protocolo OAuth 2.0.

### <a name="BKMK_MFA"></a>Multi-Factor Authentication (MFA) e Azure RMS
Para usar o Multi-Factor Authentication (MFA) com o Azure RMS, é necessária uma das seguintes opções:

-   Office 2013 (versão mínima):

    -   Se você tiver o Office 2013, instale também a [atualização para o Office 2013 (KB3054853) de 9 de junho de 2015](https://support.microsoft.com/kb/3054853). Para obter mais informações sobre esta atualização e sobre a forma como o início de sessão no Office 2013 baseado no Active Directory Authentication Library (ADAL) torna a autenticação moderna, consulte [Visualização pública de autenticação moderna do Office 2013 anunciada](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) no blog do Office.

-   Aplicativo Rights Management sharing para Windows:

    -   Você deve ter instalada a versão mínima do 1.0.1908.0, que pode ser confirmada através do Painel de controle, Programas e Recursos. Para obter mais informações sobre o aplicativo de compartilhamento, consulte [Aplicativo de compartilhamento Rights Management para Windows](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   Aplicativo Rights Management sharing para dispositivos móveis e computadores Mac:

    -   Certifique-se de que tenha a versão mais recente instalada. O suporte a MFA entrou em vigor na versão de setembro de 2015 do aplicativo RMS sharing.

Em seguida, configure sua solução MFA:

-   Para locatários gerenciados pela Microsoft (necessário Active Directory do Azure ou Office 365):

    -   Configure o Azure MFA para impor o MFA para usuários. Para obter instruções, consulte [Introdução ao Azure Multi-Factor Authentication na nuvem](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) na documentação do Azure.

        Para obter mais informações sobre o Azure MFA, consulte [O que é o Azure Multi-Factor Authentication?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Para locatários federados (você opera servidores de federação no local):

    -   Configure seus servidores de federação do Active Directory do Azure ou Office 365. Por exemplo, se você estiver usando o AD FS, consulte [Configurar métodos de autenticação adicionais do AD FS](https://technet.microsoft.com/library/dn758113.aspx) no TechNet.

        Para obter mais informações sobre esse cenário, consulte [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) no blog do Office.

## <a name="BKMK_SupportedDevices"></a>Dispositivos cliente que suportam o Azure RMS
Use as seções a seguir para identificar quais dispositivos oferecem suporte ao Azure Rights Management (RMS) e para quais recursos do RMS eles oferecem suporte:

-   [Computadores](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Dispositivos móveis](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Recursos do dispositivo cliente](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Computadores
Os seguintes sistemas operacionais de computador suportam o Azure Rights Management:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Mac OS X**: Versão mínima do Mac OS X 10.8 (Mountain Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Dispositivos móveis
Os seguintes sistemas operacionais de dispositivos móveis suportam o Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Telefones e tablets Android**: Versão mínima do Android 4.0.3

-   **iPhone e iPad**: Versão mínima do iOS 7.0

-   **Tablets Windows RT**: Windows 8 RT, Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Recursos do dispositivo cliente
Nem todos os dispositivos cliente com suporte oferecem suporte a todos os recursos RMS. Use a seguinte tabela para identificar quais aplicativos oferecem suporte aos recursos RMS e as exceções.

A menos que indique o contrário, os recursos com suporte se aplicam ao Azure RMS e ao AD RMS. Além disso, o suporte AD RMS no iOS, Android, OS X e Windows Phone 8.1 requer [Extensão de Dispositivo Móvel do Active Directory Rights Management Services](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

Informações sobre as colunas da tabela:

-   **PDF Protegido**: Os arquivos que têm extensão de nome de arquivo .ppdf e que são criados automaticamente quando você usa o aplicativo de compartilhamento do RMS para compartilhar arquivos do Office e arquivos PDF por email. O aplicativo de compartilhamento do RMS inclui um leitor para arquivos PDF protegidos. Anteriormente, se você criou arquivos PDF que foram protegidos usando o Azure RMS ou o AD RMS, poderá continuar a ler esses arquivos nos dispositivos Windows, iOS e Android usando o Foxit Reader e o Nitro Pro.

-   **Email:** Os clientes de email listados podem proteger a mensagem de email por si próprios, isso protegerá automaticamente quaisquer arquivos anexados. Neste cenário, o recurso de pré-visualização do cliente pode exibir o conteúdo protegido (mensagem e anexo) para os destinatários autorizados. No entanto, se uma mensagem de email por si só não estiver protegida, mas o anexo estiver protegido, o recurso de visualização do cliente não poderá exibir o anexo protegido para os destinatários autorizados.

-   **Outros tipos de arquivos**: Arquivos de texto e imagem incluem arquivos com uma extensão de nome de arquivo como .txt, .xml, .jpg e jpeg. Esses arquivos alteram sua extensão de nome de arquivo depois de serem protegidos nativamente pelo RMS, tornando-se somente leitura. Os arquivos que não podem ser protegidos nativamente têm uma extensão do nome de arquivo .pfile após serem protegidos genericamente pelo RMS. Para obter mais informações, consulte as seções [Níveis de proteção - nativa e genérica](https://technet.microsoft.com/library/dn339003.aspx) e [Tipos de arquivos com suporte e extensões de nome de arquivo](https://technet.microsoft.com/library/dn339003.aspx) do[Guia do Administrador do Aplicativo de Compartilhamento do Rights Management](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Sistema operacional do dispositivo**|Word, Excel, PowerPoint|PDF protegido|Email|Outros tipos de arquivos|
|------------------------------------------|---------------------------|-----------------|---------|----------------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Aplicativos móveis do Office (somente Azure RMS) <sup>1</sup><br /><br />Office Online<sup>2</sup>|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client para Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplicativo de compartilhamento do RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web App (OWA)<sup>3</sup><br /><br />Windows Mail<sup>4</sup>|Aplicativo de compartilhamento RMS para Windows Texto, imagens, pfile<br /><br />Siemens JT2Go: Arquivos JT (apenas Windows 10)|
|**iOS**|Office para iPad e iPhone<sup>5</sup><br /><br />Office Online<sup>2</sup><br /><br />TITUS Docs|Foxit Reader<br /><br />Aplicativo RMS sharing<sup>1</sup><br /><br />TITUS Docs|NitroDesk<sup>4</sup><br /><br />Outlook para iPad e iPhone<sup>4</sup><br /><br />OWA para iOS<sup>3</sup><br /><br />Proteger Ilhas IQProtector<sup>1</sup><br /><br />TITUS Mail|Aplicativo RMS sharing<sup>1</sup>: Texto, imagens, pfile<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App para Android<br /><br />Office Online<sup>2</sup>|GigaTrust App para Android<br /><br />Foxit Reader<br /><br />Aplicativo RMS sharing<sup>1</sup>|9Folders<sup>4</sup><br /><br />GigaTrust App for Android<sup>4</sup><br /><br />NitroDesk<sup>4</sup><br /><br />OWA para Android<sup>3</sup> <sup>6</sup><br /><br />Samsung Email (S3 e posterior)<sup>6</sup><br /><br />Proteger Ilhas IQProtector<sup>1</sup><br /><br />Classificação TITUS para dispositivos móveis|Aplicativo RMS sharing<sup>1</sup>: Texto, imagens, pfile|
|**OS X**|Office 2011 (somente do AD RMS)<br /><br />Office 2016 para Mac<br /><br />Office Online<sup>2</sup>|Foxit Reader<br /><br />Aplicativo RMS sharing<sup>1</sup>|Outlook 2011 (somente do AD RMS)<br /><br />Outlook 2016 para Mac<br /><br />Outlook para Mac|Aplicativo RMS sharing<sup>1</sup>: Texto, imagens, pfile|
|**Windows RT**|Office 2013 RT<br /><br />Office Online<sup>2</sup>|Sem suporte|Outlook 2013 RT<br /><br />Aplicativo de e-mail para o Windows<br /><br />Windows Mail<sup>4</sup>|Siemens JT2Go: Arquivos JT|
|**Windows Phone 8.1**|Office Móvel (somente do AD RMS)|Aplicativo RMS sharing<sup>1</sup>|Outlook Mobile<sup>4</sup>|Aplicativo RMS sharing<sup>1</sup>: Texto, imagens, pfile|
|**Blackberry 10**|Sem suporte|Sem suporte|Email Blackberry<sup>4</sup>|Sem suporte|
<sup>1</sup> oferece suporte à exibição de conteúdo protegido.

<sup>2</sup> oferece suporte à exibição de conteúdo protegido no SharePoint Online, OneDrive for Business e Outlook Web Access.

<sup>3</sup> se um destinatário tem uma caixa de correio no Exchange no local e recebe um email protegido, esse conteúdo pode ser aberto apenas em um cliente de email com formatação, como o Outlook.  Esse conteúdo não pode ser aberto no Outlook Web Access.

<sup>4</sup> usa o Exchange ActiveSync IRM, que deve ser habilitado pelo administrador do Exchange. Os usuários podem exibir, responder e responder a todos para mensagens de email protegidas, mas os usuários não podem proteger novas mensagens de email.

Se um destinatário tem uma caixa de correio no Exchange no local e recebe um email protegido de outra organização que usa Exchange, esse conteúdo pode ser aberto apenas em um cliente de email com formatação, como o Outlook.  Esse conteúdo não pode ser aberto em um dispositivo que usa o Exchange Active Sync IRM.

<sup>5</sup> dá suporte à exibição e edição de documentos protegidos. Para obter mais informações, consulte a seguinte postagem no blog do Office: [Suporte para Azure Rights Management chega ao Office para iPad e iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>6</sup> para obter mais informações, consulte a seguinte postagem no blog do Office: [OWA para Android já disponível em dispositivos selecionados](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Para obter mais informações sobre suporte futuro do RMS para Office em outras plataformas, consulte a seguinte postagem do blog do Office: [Office em qualquer lugar, criptografia em qualquer lugar](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Aplicativos que suportam o Azure RMS
Os seguintes aplicativos suportam o Azure RMS nativamente, o que significa que o RMS é totalmente integrado a esses aplicativos usando as APIs do RMS para suportar as restrições de uso. Esses aplicativos também são conhecidos como aprimorados pelo RMS:

-   **Aplicativos do Microsoft Office**(Word, Excel, PowerPoint e Outlook) dos pacotes a seguir podem proteger conteúdo usando o Azure RMS:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise E4

    -   Office 365 Enterprise E5

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Outras edições do Office (com exceção do Office 2007) podem consumir o conteúdo protegido.

    > [!NOTE]
    > Azure RMS com o Office Professional Plus 2010 ou o Office Professional 2010:
    > 
    > -   Requer o aplicativo de compartilhamento do Rights Management para Windows
    > -   Sem suporte no Windows 10

-   **O aplicativo de compartilhamento do Rights Management para Windows**

    Para obter mais informações sobre o aplicativo de compartilhamento do Rights Management do Windows, consulte os seguintes recursos:

    -   [Guia do administrador do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Guia do usuário do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

-   **O aplicativo de compartilhamento do Rights Management para plataformas móveis**

    Para obter mais informações sobre o aplicativo de compartilhamento do Rights Management para plataformas móveis, consulte os seguintes recursos:

    -   Baixe o aplicativo relevante usando os links na [página do Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Se gerenciar dispositivos móveis usando o Microsoft Intune, você poderá implantar e configurar o aplicativo em [dispositivos iOS e Android como aplicativo gerenciado por políticas](https://technet.microsoft.com/library/dn878026.aspx).

    -   [Perguntas frequentes para os aplicativos de compartilhamento do Microsoft Rights Management para Plataformas Móveis](http://technet.microsoft.com/dn451248)

-   **Outros aplicativos que oferecem suporte às APIs do RMS**:

    -   Aplicativos de linha de negócios que são gravados internamente, usando o SDK do RMS

    -   Aplicativos de fornecedores de software que são gravados usando o SDK do RMS

    Para obter mais informações sobre o SDK, consulte o [SDK do Microsoft Rights Management](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> Os seguintes aplicativos não são atualmente suportados pelo Azure RMS:
> 
> -   Microsoft Office para Mac 2011
> -   Microsoft OneDrive for Business para o SharePoint Server 2013
> -   Visualizador XPS
> 
> Além disso, o aplicativo de compartilhamento do RMS tem as seguintes restrições:
> 
> -   Para computadores Windows: Requer uma versão mínima do Windows 7 Service Pack 1

Para mais informações sobre como esses aplicativos oferecem suporte ao Azure RMS, consulte [Como os aplicativos dão suporte ao Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Para obter informações sobre como configurá-los, consulte [Configurando aplicativos do Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>Servidores no local que suportam o Azure RMS
Os seguintes produtos de servidor local são suportados com o Azure RMS ao usar o conector Azure RMS, que atua como uma interface de comunicação entre os servidores locais e o Azure RMS (um retransmissor). Além disso, essa configuração requer uma configuração da sincronização de diretório entre as florestas do Active Directory e do Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Servidores de arquivos que executam o Windows Server e usam a FCI (Infraestrutura de Classificação de Arquivos)**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Como os servidores de arquivo que executam o Windows Server 2008 R2 não têm uma ação de tarefa de gerenciamento de arquivos interna para aplicar a proteção RMS, você não pode usar o conector RMS para esse cenário. No entanto, você pode usar a Infraestrutura de Classificação de Arquivos e o Azure RMS nesses sistemas operacionais se você configurar uma tarefa de gerenciamento de arquivos personalizada para executar um script ou executável que podem proteger arquivos usando o Azure RMS. Por exemplo, um script do Windows PowerShell que usa os [cmdlets RMS Protection](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Você também pode usar esses cmdlets com servidores que executam versões posteriores do Windows Server, com o benefício de que esses cmdlets conseguem proteger todos os tipos de arquivo. O conector RMS protege apenas arquivos do Office. Para instruções, consulte [Proteção por RMS com a Infraestrutura de Classificação de Arquivos &#40;FCI&#41; do Windows Server](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

O conector RMS é suportado no Windows Server 2012 R2, no Windows Server 2012 e no Windows Server 2008 R2.

Para obter mais informações sobre como configurar o conector RMS para esses servidores locais, consulte [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Consulte também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

