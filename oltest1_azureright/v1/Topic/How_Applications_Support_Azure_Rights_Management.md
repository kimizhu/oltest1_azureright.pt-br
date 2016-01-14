---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Como os aplicativos d&#227;o suporte ao Azure Rights Management
Use as seguintes informações para ajudar a entender como os aplicativos de usuário final (como os aplicativos Office, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e SharePoint) podem usar a Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para ajudar a proteger os dados da sua organização:

-   [Aplicativo de compartilhamento RMS para Windows e plataformas móveis](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Aplicativos do Office: Word, Excel, PowerPoint, Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online e Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online e SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [Servidores de arquivos que executam o Windows Server e usam o File Classification Infrastructure (FCI)](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Outros aplicativos que dão suporte às APIs do RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Para verificar os aplicativos e as versões que o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) suporta, consulte [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

Em alguns casos, a proteção de informações é aplicada automaticamente, de acordo com as políticas que você configurar. Por exemplo, esse é o caso de bibliotecas do SharePoint, arquivos confidenciais e regras de transporte do Exchange. Em outros casos, os usuários devem aplicar a proteção das informações diretamente em seus aplicativos, seja selecionando um modelo ou opções específicas. Por exemplo, este é o caso quando os usuários compartilham um arquivo por email ou protegem um arquivo no local, restringindo o acesso ou o uso a usuários selecionados ou usuários fora da organização.

Os modelos facilita para os usuários (e administradores que configuram políticas) a aplicação do nível correto de proteção e restringir o acesso a pessoas dentro de sua organização. Embora o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] seja fornecido com dois modelos padrão, é recomendável criar modelos personalizados para reduzir as ocasiões em que eles precisam especificar as opções individuais. Para obter mais informações, consulte [Configurando modelos personalizados do Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

Para os casos em que os próprios usuários devem aplicar as informações de proteção, lembre-se de dar orientações e instruções sobre como e quando fazer isso. As instruções devem ser específicas para o aplicativo e as versões que eles usam e como usam, e as orientações sobre quando e como aplicar as informações de proteção devem ser adequadas para seu negócio. Para obter mais informações, consulte [Ajudar aos usuários a proteger os arquivos usando o Azure Rights Management](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Para obter informações sobre como configurar aplicativos para o Azure RMS, consulte [Configurando aplicativos do Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Para obter exemplos e capturas de tela de aplicativos usando o Azure RMS, consulte a seção [O Azure RMS em ação: O que administradores e usuários veem](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) do tópico [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md).

## <a name="BKMK_SharingAppIntro"></a>Aplicativo de compartilhamento RMS para Windows e plataformas móveis
O aplicativo de compartilhamento de RMS é um aplicativo gratuito, que pode ser baixado e que é necessário para suportar o Office 2010, mas também recomendado para computadores com Windows, computadores MAC e dispositivos móveis. Uma das suas vantagens é que ele pode aplicar proteção genérica para aplicativos e arquivos que não dão suporte ao [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] nativamente, o que significa que todos os arquivos podem ser protegidos. Para obter mais informações sobre os diferentes níveis de proteção, consulte a seção [Nível de proteção: nativa e genérica](http://technet.microsoft.com/library/dn339003.aspx)do tópico [guia de administrador do aplicativo de compartilhamento do Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

Quando os usuários protegem seus arquivos usando o aplicativo de compartilhamento de RMS podem também controlar os documentos protegidos e se necessário, revogar o acesso a eles. Eles fazem isso usando o [site de acompanhamento de documento](http://go.microsoft.com/fwlink/?LinkId=529562).

Para computadores Windows, o aplicativo de compartilhamento RMS se integra de maneira discreta e melhora os aplicativos que os usuários já utilizam:

-   É instalado um complemento do Office para Word, Excel, PowerPoint e Outlook. Isso fornece aos usuários um botão **Compartilhamento Protegido** na faixa de opções, que chama uma caixa de diálogo de configurações fácil de usar que são mais comumente usadas para proteger os arquivos a serem enviados. Esse botão também fornece uma maneira rápida de acessar o site de acompanhamento de documento.

-   Uma nova opção de clicar com o botão direito do mouse para o Explorador de Arquivos. Isso fornece aos usuários uma opção de **Proteção in-loco**, que chama uma caixa de diálogo de configurações fácil de usar que são mais comumente usadas para proteger os arquivos armazenados em um disco.

-   Um visualizador para abrir arquivos que foram protegidos pelo [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Esse visualizador será automaticamente invocado quando não houver outro aplicativo instalado que possa abrir o arquivo protegido.

-   Configuração de back-end para o Office 2010 que permite que o Word, o Excel, o PowerPoint e o Outlook deste pacote funcionem perfeitamente com o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Embora o compartilhamento de aplicativos para Windows RMS possa ser baixado e instalado para um único computador usando a [página do Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), ele também suporta uma implantação corporativa para instalação silenciosa e configuração personalizada. Para obter mais informações, consulte os seguintes recursos:

-   [Guia do administrador do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339003.aspx)

-   [Guia do usuário do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

O aplicativo de compartilhamento RMS para dispositivos móveis é compatível com os dispositivos móveis utilizados com mais frequência, como iPad e iPhone, Android, Windows Phone e Windows RT. Os usuários podem baixar esse aplicativo da loja relevante, e há links para elas na [página do Gerenciamento de Direitos Microsoft](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Aplicativos do Office: Word, Excel, PowerPoint, Outlook
Esses aplicativos dão suporte nativamente ao Gerenciamento de Direitos usando Gerenciamento de Direitos de Informação (IRM) e permitem que os usuários apliquem proteção a um documento salvo ou a uma mensagem de email a ser enviada. Os usuários podem aplicar modelos ou escolher configurações bem personalizadas de acesso, direitos e restrições de uso. Por exemplo, os usuários podem configurar um arquivo para que ele possa ser acessado somente por pessoas de sua organização, ou controlar se o arquivo pode ser editado ou restrito a somente leitura, ou impedir que ele seja impresso. Para arquivos que têm data para vencer, pode ser configurada uma data de validade (diretamente por usuários ou aplicando um modelo) para quando o arquivo não puder mais ser acessado. Para o Outlook, os usuários também podem escolher a opção **Não Encaminhar** para ajudar a impedir o vazamento de dados.

### <a name="BKMK_ExchangeIntro"></a>Exchange Online e Exchange Server
Ao usar o Exchange Online ou o Exchange Server, você pode usar a integração de gerenciamento de direitos de informação (IRM), que fornece soluções de proteção de informações adicionais:

-   **IRM do Exchange ActiveSync** para que os dispositivos móveis possam proteger e consumir mensagens de email protegidas.

-   O suporte RMS para o **Outlook Web App**, implementado de forma semelhante ao cliente Outlook, de modo que os usuários possam proteger as mensagens de email por modelos ou especificando as opções individuais, e os usuários possam ler e usar emails protegidos enviados a eles.

-   **Regras de proteção** para clientes Outlook configuradas por um administrador para aplicar automaticamente modelos de RMS às mensagens de email para destinatários especificados. Por exemplo, quando emails internos forem enviados ao seu departamento jurídico, eles só poderão ser lidos por membros do departamento jurídico e não poderão ser encaminhados. Os usuários veem a proteção aplicada à mensagem de email antes de enviá-la e, por padrão, eles podem removê-la se decidirem que não é necessária. Os emails são criptografados antes de serem enviados. Para obter mais informações, consulte [Regras de Proteção do Outlook](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [Criar uma regra de proteção do Outlook](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   As **Regras de transporte** que um administrador configura para aplicar automaticamente os modelos de RMS às mensagens de email com base em propriedades como: remetente, destinatário, assunto da mensagem e conteúdo. Elas são semelhantes ao conceito de regras de proteção, mas não permitem que os usuários removam a proteção, podem ser aplicadas ao Outlook Web Access e emails enviados por dispositivos móveis e não criptografa mensagens de email antes que sejam enviados do cliente. Para obter mais informações, consulte [Criar uma regra de proteção de transporte](http://technet.microsoft.com/library/dd302432.aspx) na biblioteca do Exchange.

-   **Políticas de prevenção de perda de dados (DLP)** que contêm conjuntos de condições para filtrar mensagens de email e tomar medidas para ajudar a evitar a perda de dados para conteúdos confidenciais (por exemplo, informações pessoais ou informações de cartão de crédito). As dicas de política podem ser usadas quando forem detectados dados confidenciais, para alertar os usuários que eles talvez precisem aplicar a proteção de informações, com base nas informações na mensagem de email. Para obter mais informações, consulte [Prevenção de perda de dados](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   A **Criptografia de mensagem do Office 365** que usa regras de transporte para enviar emails criptografados para pessoas de fora da empresa e o email é lido em um navegador com uma interface semelhante ao Outlook Web App. Você pode personalizar o texto de aviso e o texto do cabeçalho em emails criptografados de sua empresa, e até mesmo adicionar o logotipo da empresa. Para obter mais informações, consulte [Criptografia de mensagens do Office 365](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) no site do Office.

Se usar o Exchange Server, você poderá usar os recursos de proteção de informações com o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] implantando o conector de RMS, que atua como um retransmissor entre os servidores no local e o serviço de nuvem do RMS. Para obter mais informações, consulte [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online e SharePoint Server
Ao usar o SharePoint Online ou o SharePoint Server, você pode usar a integração de gerenciamento de direitos de informação (IRM), que permite que os administradores protejam listas ou bibliotecas, para que um arquivo fique protegido quando um usuário fechá-lo e apenas pessoas autorizadas possam visualizar e usar o arquivo de acordo com as políticas de proteção de informações especificadas. Por exemplo, o arquivo pode ser somente leitura, pode desativar a cópia de texto, pode impedir que uma cópia local seja salva e pode evitar a impressão do arquivo.

Para listas e bibliotecas, a proteção de informações é sempre aplicada por um administrador, nunca um usuário final. E isso é aplicado no nível de lista ou biblioteca para todos os documentos desse contêiner, e não em arquivos individuais.  Se você usar o SharePoint Online, os usuários também podem aplicar IRM para a sua biblioteca de Negócios OneDrive.

O serviço IRM deve primeiro ser habilitado para o SharePoint. Em seguida, especifique o Gerenciamento de Direitos de Informação para uma biblioteca. No caso do SharePoint Online e OneDrive para Negócios, os usuários podem especificar também Gerenciamento de Direitos de Informação do seu OneDrive para a biblioteca de Negócios. O SharePoint não usa modelos de política de direitos, embora haja definições de configuração do SharePoint para selecionar que se aproximam daquelas que você pode especificar em modelos.

Se usar o SharePoint Server, você poderá usar os recursos de proteção de informações com o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] implantando o conector de RMS, que atua como um retransmissor entre os servidores no local e o serviço de nuvem do RMS. Para obter mais informações, consulte [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> Atualmente, existem algumas limitações quando você usa o IRM com o SharePoint:
> 
> -   Você não pode usar os modelos padrão ou personalizados que você gerencia no Azure Classic Portal.
> -   Arquivos que tenham uma extensão .PPDF para arquivos PDF protegidos, não são suportados. Arquivos que possuem extensão .PDF e que foram protegidos nativamente pelo RMS têm suporte quando você usa um leitor PDF que oferece suporte nativo ao RMS.
> -   Como ainda não há suporte para RMS no Office em dispositivos móveis, esses dispositivos devem usar um navegador para exibir arquivos que foram protegidos por RMS e os arquivos que são somente para leitura.

O Azure RMS aplica restrições de uso e criptografia de dados quando os documentos são baixados pelo SharePoint e não quando o documento é criado pela primeira vez no SharePoint ou carregado na biblioteca. Para obter informações sobre como os documentos são protegidos antes de serem baixados, veja [Criptografia de Dados no OneDrive for Business e SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) na documentação do SharePoint.

Para obter mais informações sobre como usar o Azure RMS com o SharePoint, consulte a publicação do blog do Office a seguir: [Novidades no Gerenciamento de Direitos de Informação do SharePoint e do SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>Servidores de arquivos que executam o Windows Server e usam o File Classification Infrastructure (FCI)
Ao configurar o Windows Server para usar o File Classification Infrastructure, este recurso de Gerenciador de Recursos do Servidor de Arquivos pode verificar os arquivos e determinar se eles contêm dados confidenciais. Os arquivos que atendem a esse critério são marcados com propriedades de classificação definidas por um administrador. O File Classification Infrastructure poderá então agir de forma automática, de acordo com a classificação. Uma dessas ações inclui aplicar proteção de informações usando [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] e a implantação do conector de Gerenciamento de Direitos de Informação (também conhecido como conector RMS). Os arquivos do Office serão então automaticamente protegidos pelo Azure RMS.

Para proteger todos os tipos de arquivo, não use o conector RMS, mas em vez disso, execute um script do Windows PowerShell, usando os cmdlets da [ferramenta de proteção do RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

As políticas de classificação são totalmente configuráveis ​​e altamente extensíveis para que você possa evitar possíveis vazamentos de dados de usuários não autorizados e autorizados. Elas também podem ajudar a reduzir o risco de vazamento de dados por administradores de rede, pois você pode configurar políticas que não exigem que esses administradores tenham acesso aos arquivos.

Para instruções de como implantar e configurar o conector RMS para arquivos do Office, consulte [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

Para instruções de como usar o script do Windows PowerShell para todos os tipos de arquivos, consulte [Proteção por RMS com a Infraestrutura de Classificação de Arquivos &#40;FCI&#41; do Windows Server](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Outros aplicativos que dão suporte às APIs do RMS
Usando o SDK do RMS, os desenvolvedores podem gravar seus aplicativos internos de linha de negócios com suporte nativo do [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. A integração da proteção de informações com esses aplicativos depende de como eles são gravados. Por exemplo, a integração pode ser automaticamente aplicada com uma exigência de interação mínima do usuário, ou, para uma experiência mais personalizada, os usuários podem ser solicitados a definir configurações para aplicar proteção de informações a arquivos. Para obter mais informações sobre o SDK, consulte o [SDK do Microsoft Rights Management](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

Da mesma forma, muitos fornecedores de software oferecem aplicativos para dar soluções de proteção de informações, também conhecidos como produtos de gerenciamento de direitos corporativos (ERM). Um exemplo conhecido é um leitor de PDF que suporta[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] para plataformas específicas. Você pode usar a tabela na seção [Recursos do dispositivo cliente](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) do tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) para identificar os aplicativos que oferecem suporte ao RMS (aplicativos aprimorados pelo RMS) e, em seguida, usar uma pesquisa na Web para comprar ou baixar o aplicativo.

> [!TIP]
> Para aplicativos recém lançados, verifique os canais comunitários RMS, listados em [Informações e suporte para o Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Consulte também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

