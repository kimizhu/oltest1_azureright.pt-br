---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Perguntas frequentes sobre o Azure Rights Management
Algumas perguntas frequentes sobre o Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], também conhecido como Azure RMS:

## O que eu preciso para implantar o Azure RMS e como faço para prosseguir?
Primeiro, verifique o [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md), que tem informações sobre as opções de assinatura da nuvem, como você pode usar seus servidores locais com o Azure RMS, quais cenários de implantação não têm suporte atualmente, quais dispositivos e aplicativos dão suporte ao Azure RMS, e um link caso você necessite de uma lista de endereços IP e de nomes de domínio para firewalls ou para servidores de proxy. Talvez você também queira verificar os outros tópicos da seção [Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) para obter um entendimento básico de como o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pode ajudar a proteger os dados da sua organização, como ele funciona com aplicativos, como ele se compara à versão local do Active Directory Rights Management e compreender os termos e abreviações que são específicos do [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Em seguida, quando estiver pronto para testar o Azure RMS para si mesmo, ou para implantá-lo para a sua organização, use o[Roteiro de implantação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para obter uma lista de etapas com links para mais informações e instruções.

Se você precisar de informações adicionais, recursos e opções de suporte, consulte [Informações e suporte para o Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Posso integrar o Azure RMS com meus servidores locais?
Sim. O Azure RMS pode ser integrado com seus servidores locais, como servidores de arquivos do Exchange Server, SharePoint e Windows. Para fazer isso, use o [conector do Rights Management](https://technet.microsoft.com/library/dn375964.aspx). Ou, se você está interessado apenas em usar a FC (Infraestrutura de Classificação de Arquivos) com o Windows Server, você pode usar os [cmdlets de Proteção do RMS](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Você também pode sincronizar e federar seus controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais transparente para os usuários, por exemplo, usando o [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

O Azure RMS gera e gerencia automaticamente certificados XrML, conforme necessário, para que ele não use uma PKI local. Para obter mais informações sobre como o Azure RMS usa certificados, consulte a seção [Passo a passo de como funciona o Azure RMS: Primeiro uso, proteção de conteúdo, consumo de conteúdo](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) no tópico [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md).

## Eu tenho uma implantação híbrida do Exchange com alguns usuários no Exchange Online e com outros no Exchange Server — isto é compatível com o Azure RMS?
Com certeza, e o melhor é que os usuários serão capazes de proteger e consumir emails e anexos protegidos entre as duas implantações do Exchange. Para essa configuração, [ative o Azure RMS](https://technet.microsoft.com/library/jj658941.aspx) e [habilite o IRM para o Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx) e, em seguida, [implante e configure o conector RMS](https://technet.microsoft.com/library/dn375964.aspx) para o Exchange Server.

## Se eu implantar o Azure RMS em produção, a minha empresa fica então "bloqueada" na solução ou corre o risco de perder o acesso ao conteúdo que protegemos com o Azure RMS?
Não, você sempre permanece no controle de seus dados e pode continuar a acessá-los, mesmo se decidir não usar o Azure RMS. Para obter mais informações, consulte [Encerramento e desativação do Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

No entanto, antes de encerrar sua implantação do Azure RMS, gostaríamos de ouvi-lo para compreender por que tomou esta decisão. Se o Azure RMS não atende seus requisitos de negócios, verifique conosco se uma nova funcionalidade está planejada para um futuro próximo ou se existem alternativas. Envie um email para [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) e teremos todo o gosto em analisar seus requisitos técnicos e comerciais.

## É possível controlar quais dos meus usuários podem usar o Azure RMS para proteger o conteúdo?
Sim, o Azure RMS possui controles de integração do usuário para esse cenário. Para obter mais informações, consulte a seção [Configurando controles de integração para uma implantação em fases](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls), no tópico [Ativando o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## Posso impedir os usuários de compartilharem documentos protegidos com organizações específicas?
Um dos maiores benefícios do Azure RMS é que ele oferece suporte para colaboração de empresas sem precisar configurar confianças explícitas para cada organização parceira, porque o AD do Azure cuida da autenticação para você.

Não há nenhuma opção de administração para impedir que os usuários compartilhem com segurança os documentos com organizações específicas. Por exemplo, você deseja bloquear uma organização que não confia ou que tenha uma empresa concorrente. Impedir que o Azure RMS envie documentos protegidos aos usuários dessas organizações não faz sentido, pois os usuários podem compartilhar seus documentos desprotegidos, o que é, provavelmente, a última coisa que você quer fazer neste cenário! Por exemplo, você não será capaz de identificar quem está compartilhando documentos confidenciais da empresa com os usuários dessas organizações, que pode ser feito quando o documento (ou email) for protegido pelo Azure RMS.

## Ao compartilhar um documento protegido com alguém fora da minha empresa, como o usuário é autenticado?
O Azure RMS sempre usa uma conta do Active Directory do Azure e um endereço de email associado para autenticação de usuário, o que torna a colaboração entre empresas perfeita para administradores. Se a outra organização usar os serviços do Azure, os usuários já terão contas no Active Directory do Azure, mesmo que essas contas sejam criadas e gerenciadas no local e, em seguida, sincronizadas no Azure.  Se a organização tiver o Office 365, em segundo plano, esse serviço também usa o Active Directory do Azure para as contas de usuário.  Se a organização não tiver contas gerenciadas no Azure, os usuários podem se inscrever no [RMS para pessoas físicas](https://technet.microsoft.com/library/dn592127.aspx), o que cria um locatário do Azure não gerenciado e um diretório para a organização com uma conta de usuário, de forma que este usuário possa ser autenticado no Azure RMS.

O método de autenticação para essas contas pode variar, dependendo de como o administrador na outra organização configurou as contas do Active Directory do Azure. Por exemplo, seria possível usar senhas que foram criadas para essas contas, Multi-Factor Authentication (MFA), federação ou senhas que foram criadas nos serviços de domínio do Active Directory e, em seguida, sincronizadas com o Active Directory do Azure.

## Posso adicionar usuários de fora da minha empresa aos modelos personalizados?
Sim.  Ao criar modelos personalizados, onde os usuários finais (e os administradores) possam selecionar aplicativos, a aplicação de proteção de informações usando políticas predefinidas que você especifica torna-se um processo rápido e fácil. Uma das configurações no modelo é a de quem está autorizado a acessar o conteúdo, e você pode especificar usuários e grupos da sua organização e usuários fora da sua organização.

Para especificar usuários de fora da sua organização, use o [módulo do Windows PowerShell para Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx):

-   **Use um objeto de definição de direitos para criar ou atualizar um modelo**.    Especifique os endereços de email externos e seus direitos em um objeto de definição de direitos que você usará para criar ou atualizar um modelo. É possível especificar o objeto de definição de direitos usando o cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) para criar uma variável e, em seguida, fornecer essa variável para o parâmetro -RightsDefinition com o cmdlet [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) (para um novo modelo) ou o cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) (se modificar um modelo existente). No entanto, se você está adicionando esses usuários a um modelo existente, precisará definir objetos de definição de direitos para os grupos existentes nos modelos e não apenas os usuários externos.

Para obter mais informações sobre modelos personalizados, consulte [Configurando modelos personalizados do Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## A quais dispositivos e tipos de arquivos o Azure RMS oferece suporte?
Para obter uma lista de dispositivos com suporte, consulte a seção [Dispositivos cliente que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices), no tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md). Como nem todos os dispositivos com suporte podem atualmente dar suporte a todos os recursos RMS, verifique também a tabela [Recursos do dispositivo cliente](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities), no mesmo tópico.

O Azure RMS oferece suporte a todos os tipos de arquivo. Para arquivos de texto, imagem, do Microsoft Office (Word, Excel, PowerPoint), .pdf e para tipos de arquivo de alguns outros aplicativos, o Azure RMS oferece proteção nativa que inclui criptografia e aplicação de direitos (permissões). Para todos os outros aplicativos e tipos de arquivo, a proteção genérica oferece encapsulamento de arquivos e autenticação para verificar se um usuário está autorizado a abrir o arquivo.

Para obter uma lista de extensões de nomes de arquivos que com suporte nativo pelo Azure RMS, consulte a seção [Tipos de arquivos e extensões de nome de arquivos com suporte](http://technet.microsoft.com/library/dn339003.aspx) no [guia de administrador do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339003.aspx). As extensões de nome de arquivo não listadas têm suporte através do uso do aplicativo de compartilhamento RMS, que automaticamente aplica a proteção genérica a esses arquivos.

## Quando você oferecerá suporte a migração do AD RMS?
Inicialmente, o Azure RMS não oferece suporte à migração de uma implantação local do Rights Management, como o AD RMS. Mas agora há suporte.

Para obter mais informações, consulte [Migrando do AD RMS para o Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## Nós desejamos muito usar o BYOK com o Azure RMS, mas sabemos que isso não é compatível com o Exchange Online. O que vocês sugerem?
Não deixe que essa limitação atual atrase a sua implantação do Azure RMS. Se você possui o Exchange Online e deseja usar sua própria chave (BYOK), recomenda-se implantar o Azure RMS no modo padrão de gerenciamento de chaves agora, em que a Microsoft gera e gerencia sua chave. Dessa forma, você obtém todos os benefícios de proteger seus arquivos importantes e emails agora, com a opção de mudar para BYOK posteriormente (por exemplo, quando o Exchange Online oferecer suporte a BYOK).

No entanto, se as políticas de sua empresa exigem que você use um módulo de segurança de hardware (HSM), o que bloquearia a implantação do Azure RMS, outra opção será implantar o Azure RMS com BYOK agora, com funcionalidade reduzida do RMS para o Exchange. Para obter mais informações, consulte a seção [Preços e restrições do BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing), no tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## Um recurso que estou procurando não parece funcionar com as bibliotecas protegidas do SharePoint — o suporte para meu recurso está planejado?
Atualmente, o SharePoint oferece suporte aos documentos protegidos por RMS usando as bibliotecas protegidas por IRM que não oferecem suporte a modelos personalizados, rastreamento de documentos e outros recursos.  Para obter mais informações, expanda a seção [SharePoint Online e OneDrive para a empresa: Configuração do IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) no tópico [Como os aplicativos dão suporte ao Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Se você estiver interessado em um recurso específico que ainda não é suportado, fique atento aos anúncios no [blog da equipe do RMS](http://blogs.technet.com/b/rms/).

## Como configurar o OneDrive for Business no SharePoint Online para que os usuários possam compartilhar com segurança seus arquivos com pessoas dentro e fora da empresa?
Por padrão, como um administrador do Ofice 365, você não configura isto, os usuários o fazem.

Da mesma forma que o administrador de site do SharePoint habilita e configura o IRM para uma biblioteca do SharePoint que ele tem, o OneDrive for Business é criado para os usuários habilitarem e configurarem o IRM para sua própria biblioteca do OneDrive for Business.  No entanto, usando o PowerShell, você pode fazer isso por eles. Para obter instruções, expanda a seção [SharePoint Online e OneDrive para a empresa: Configuração do IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) no artigo [Configurando aplicativos do Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## Você tem alguma dica ou truque para uma implantação bem-sucedida do RMS?
Após supervisionar muitas implantações e ouvir nossos clientes, parceiros, consultores e engenheiros de suporte – uma das maiores dicas que podemos passar por experiência: **Projetar e implantar políticas de direitos simples**.

Como o Azure RMS oferece suporte ao compartilhamento seguro com qualquer um, você pode se dar ao luxo de ser ambicioso com o alcance da sua proteção de informações. Mas seja conservador com suas políticas de direitos. Para muitas organizações, o maior impacto nos negócios vem da prevenção de vazamento de dados aplicando-se o modelo de política de direitos padrão que restringe o acesso às pessoas na organização. Obviamente, você pode obter muito mais granulares do que isso, se for necessário — impedir que pessoas imprimam, editem, etc. Mas mantenha as restrições mais granulares, como a exceção para documentos que realmente precisam de segurança de alto nível, e não implemente mais políticas restritivas no primeiro dia, apenas planeje uma abordagem mais gradual.

## Quais recursos podem ou não ser usados com as diferentes assinaturas do Azure RMS?
Para as assinaturas pagas que dão suporte ao Azure RMS (Office 365, Azure RMS Premium e Enterprise Mobility Suite), existem algumas diferenças nos recursos do RMS com suporte. Para obter uma lista delas, consulte [Comparação de Ofertas do Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

A assinatura gratuita que suporta o Azure RMS (RMS para pessoas físicas) suporta o consumo do conteúdo que foi protegido pelo Azure RMS. Para obter mais informações, consulte [RMS para pessoas físicas e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Onde posso obter informações técnicas sobre a assinatura gratuita do Azure RMS (RMS para pessoas físicas) — por exemplo, como ele realmente funciona, como assumir o controle das contas e quais domínios não podem ser usados?
Você encontrará respostas para essas perguntas no tópico [RMS para pessoas físicas e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Como podemos recuperar o acesso a arquivos que foram protegidos por um funcionário que saiu da organização?
Use o recurso de superusuário do Azure RMS, que permite que os usuários autorizados tenham direitos totais de proprietário para todas as licenças de uso que foram concedidas pelo locatário do RMS da sua organização. Esse mesmo recurso permite a serviços autorizados criarem índices e inspecionarem arquivos, conforme necessário.

Para obter mais informações, consulte [Configurando os superusuários para o Azure Rights Management e os Serviços de Descoberta ou a Recuperação de Dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## O Rights Management pode prevenir capturas de tela?
O Rights Management bloqueia capturas de tela da maioria das ferramentas de captura de tela mais comuns, o que podem ajudar a evitar a divulgação acidental ou negligente de informações confidenciais ou sensíveis. No entanto, há muitas maneiras que um usuário pode compartilhar dados que são exibidos em uma tela, e fazer uma captura de tela é apenas um método. Por exemplo, um usuário com intenção de compartilhar informações exibidas pode tirar uma foto dela usando a câmera do celular, digitando os dados novamente ou, simplesmente, retransmitindo-a verbalmente a alguém.

Como esses exemplos demonstram, somente a tecnologia não pode sempre impedir que os usuários compartilhem dados que não deveriam. Enquanto o Rights Management pode ajudar a proteger seus dados importantes usando autorização e políticas de uso, esta solução de gestão de direitos de empresa deve ser usada com outros controles. Por exemplo, implementar a segurança física, monitorar cuidadosamente as pessoas com acesso autorizado aos dados de sua organização e investir na educação do usuário para que eles entendam quais dados não devem ser compartilhados.

## Onde posso encontrar informações de suporte para o Azure RMS, tais como informações jurídicas, de conformidade e SLAs?
O Azure RMS oferece suporte a outros serviços e também se baseia em outros serviços. Se você estiver procurando por informações relacionadas ao Azure RMS, mas não sobre como usar o serviço Azure RMS, verifique os seguintes recursos:

**Informações jurídicas e de privacidade:**

-   Para obter informações sobre o contrato do Microsoft Azure: [Contrato do Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Para obter informações sobre a privacidade do Microsoft Azure: [Declaração de privacidade do Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Segurança, conformidade e auditoria:**

Consulte a seção [Requisitos de segurança, conformidade e regulamentos](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) no tópico [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md). Além disso:

-   Para certificações externas do Azure RMS: [Central de confiabilidade do Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

-   Para obter informações sobre o FIPS 140: [Validação do FIPS 140](https://technet.microsoft.com/library/security/cc750357.aspx)

**Contratos de nível de serviço (SLA – Service Level Agreement):**

-   Contrato de nível de serviço para o Azure RMS, por país selecionado: [Contrato de nível de serviço](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Contrato de nível de serviço para o Active Directory do Azure: [Contratos de nível de serviço](http://azure.microsoft.com/support/legal/sla/)

**Documentação:**

-   Site de documentação do Active Directory do Azure: [Active Directory do Azure](http://azure.microsoft.com/documentation/services/active-directory/)

-   Biblioteca do Active Directory do Azure: [Active Directory do Azure](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Biblioteca do Office 365: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## O que eu faço se a minha pergunta não estiver aqui?
Use os links e recursos listados em [Informações e suporte para o Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Além disso, há perguntas frequentes projetadas para usuários finais:

-   [FAQ do aplicativo de compartilhamento do Rights Management para Windows](https://technet.microsoft.com/dn467883)

-   [Perguntas frequentes para os aplicativos de compartilhamento do Microsoft Rights Management para Plataformas Móveis e MAC](https://technet.microsoft.com/dn451248)

-   [Perguntas Frequentes para o Controle de documentos](http://go.microsoft.com/fwlink/?LinkId=523977)

Essa página de Perguntas Frequentes será atualizada regularmente, com novas adições listadas nos anúncios mensais de atualizações na documentação no blog da [equipe Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/).

> [!TIP]
> Você pode usar a [marca de documentos](http://blogs.technet.com/b/rms/archive/tags/docs/) no blog para localizar esses anúncios de documentação mais facilmente.

## Consulte também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

