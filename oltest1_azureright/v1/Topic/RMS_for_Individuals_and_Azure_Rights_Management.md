---
description: na
keywords: na
title: RMS for Individuals and Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
---
# RMS para pessoas f&#237;sicas e Azure Rights Management
O RMS para pessoas físicas é uma assinatura gratuita de autoatendimento para usuários em uma organização que receberam arquivos confidenciais que foram protegidos pelo Microsoft Azure Rights Management (Azure RMS), mas que não podem ser autenticados porque seu departamento de TI não gerencia uma conta para os mesmos no Azure. Por exemplo, o departamento de TI não possui o Office 365 ou não usa os serviços do Azure.

Estes usuários podem criar uma conta corporativa ou de estudante gratuitamente para usar com o Azure RMS e baixar e instalar o aplicativo Rights Management sharing. Como resultado, estes usuários agora podem se autenticar para provar que são as pessoas para as quais os arquivos protegidos foram enviados e podem também ler arquivos protegidos em dispositivos móveis ou computadores.

Ao utilizar o aplicativo Rights Management sharing em computadores com Windows, estes usuários podem também proteger os arquivos no local ou enviar arquivos protegidos por email para as pessoas dentro ou fora de sua organização. Se os destinatários do email enviado estiverem em uma organização que também não gerencia contas de usuário no Azure, eles também poderão criar uma conta de pessoa física do RMS para ler o anexo de email protegido.

> [!IMPORTANT]
> Essa assinatura gratuita garante que pessoas autorizadas sempre possam ler arquivos que foram protegidos. Atualmente, você também pode usar essa assinatura gratuita para proteger documentos e criar novas mensagens de email protegidas, mas a capacidade de criar novo conteúdo protegido destina-se somente para teste e pode ser removida no futuro. Para obter mais informações e saber sobre quaisquer alterações sobre o uso do RMS para pessoa física para proteger conteúdo, consulte os [Termos de Serviço do Microsoft Rights Management](https://portal.aadrm.com/Legal/Service).

Para obter mais informações sobre como proteger os arquivos usando o aplicativo de compartilhamento Rights Management gratuito, consulte o [Guia para usuários do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339006.aspx).

O RMS para pessoas físicas é um exemplo de uma inscrição de autoatendimento que é compatível com o Active Directory do Azure. Para obter mais informações sobre como isso funciona, consulte [O que é a inscrição de autoatendimento para o Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/) na documentação do Microsoft Azure. Use as seções a seguir para obter mais informações específicas sobre o RMS para pessoas físicas:

-   [Como os usuários se inscrevem no RMS para pessoas físicas](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_SignUp)

    -   [Visão geral técnica](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TechnicalOverview)

-   [Como os administradores podem controlar as contas criadas para o RMS para pessoas físicas](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)

-   [Como saber se os usuários se inscreveram para o RMS para pessoas físicas](#BKMK_Detect)

## <a name="BKMK_SignUp"></a>Como os usuários se inscrevem no RMS para pessoas físicas
Solicite o registro para esta conta gratuita visitando a [página do Microsoft Rights Management](https://portal.aadrm.com/) e forneça seu endereço de email do trabalho ou escola. A maneira mais comum para ser direcionado para a página de inscrição é receber uma mensagem de email com um anexo protegido que contenha instruções de como se inscrever. Você receberá um email em resposta da Microsoft e, em seguida, pode concluir o processo de inscrição digitando os detalhes para criar sua conta. Quando você receber um email de confirmação da Microsoft, esta mensagem final envia o usuário para uma página onde é possível baixar o aplicativo de compartilhamento para diferentes dispositivos e um link para o guia do usuário.

#### Para se inscrever no RMS para pessoas físicas

1.  Usando um computador Windows ou Mac, vá para a [página do Microsoft Rights Management](https://portal.aadrm.com).

2.  Digite o endereço de email que você usa para sua organização, como **janetm@contoso.com** ou **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Não há suporte para contas de email pessoal, por isso não insira uma conta da Microsoft (antes conhecida como conta da Microsoft Live ID) ou outra conta pessoal que você use em casa do seu provedor de Internet.

3.  Clique em**Introdução**.

    A Microsoft usa seu endereço de email para verificar se sua organização já possui uma [assinatura paga que inclua o Azure RMS](https://technet.microsoft.com/library/dn655136.aspx). Se esse for o caso, você não precisará do RMS para pessoas físicas, por isso, você será conectado imediatamente e a assinatura de autoatendimento para o RMS para pessoas físicas será cancelada. Se uma assinatura paga do Azure RMS não for encontrada, você continuará para a próxima etapa.

4.  Aguarde uma mensagem de confirmação por email que será enviada para o endereço fornecido. Esta mensagem será da Microsoft (DoNotReply@microsoft.com) e tem como assunto **Microsoft RMS**.

5.  Ao receber o email, clique no link das instruções para concluir o processo de inscrição.

6.  O link leva você uma nova página do **Microsoft Rights Management** para fornecer detalhes da sua conta. Digite seu nome, seu sobrenome, introduza e confirme uma senha de sua escolha, selecione seu país/região (ou o país/região mais próximo, caso seu país/região não esteja na lista suspensa) e, em seguida, clique em **Criar**.

7.  Espere por outra mensagem de email da Microsoft agora confirmando que a sua conta está pronta para ser usada.

8.  Quando você receber o email, clique no link para entrar e ler as instruções para baixar e instalar o aplicativo de compartilhamento ou clique no link Ajuda para ler o guia do usuário do aplicativo de compartilhamento.

Agora que a sua conta foi criada, você pode começar a proteger arquivos e ler arquivos que outras pessoas protegeram. Ao ser solicitado a entrar para proteger ou ler arquivos protegidos, digite o endereço de email e a senha usados para criar a conta no RMS para indivíduos.

### <a name="BKMK_TechnicalOverview"></a>Visão geral técnica
O RMS para pessoas físicas usa um processo de inscrição de autoatendimento que também é usado por outros serviços que usam tecnologia baseada em nuvem da Microsoft para autenticar usuários.

Isso é o que acontece em segundo plano quando um usuário se inscreve para o RMS para indivíduos e sua organização não tiver uma assinatura do Office 365 ou assinatura do Azure e, portanto, nenhum diretório no Azure para autenticar os usuários:

1.  Quando o primeiro usuário de uma organização solicita uma assinatura do RMS para pessoas físicas, o nome de domínio fornecido em seu endereço de email é verificado para ver se ele já está associado a um locatário do Azure. Se não houver nenhum locatário existente, um novo locatário e o diretório do Azure são criados automaticamente para a organização, que contém uma conta para este primeiro usuário. Ao contrário de uma assinatura paga do Azure, essa primeira conta não é um administrador global, mas um usuário padrão. A nova conta usa o endereço de email e senha que o usuário forneceu.

    > [!NOTE]
    > Alguns nomes de domínio não podem ser usados para criar o diretório e, portanto, não podem ser usados para o RMS para indivíduos. A lista de nomes de domínios bloqueados pode ser visualizada neste arquivo do JavaScript Object Notation: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    Se for encontrado um locatário existente, será verificado se ele já possui uma assinatura do Azure RMS. Quando nenhuma assinatura é encontrada, a assinatura gratuita do RMS para pessoas físicas pode ser adicionada.

2.  A organização recebe a assinatura do RMS para pessoas físicas. Agora, esse usuário poderá ser autenticado pelo Azure e poderá proteger e ler arquivos protegidos por outras pessoas usando o Azure Rights Management. Para proteger e ler arquivos protegidos, o usuário deve ter um aplicativo habilitado para RMS, como o [aplicativo Rights Management sharing](https://technet.microsoft.com/library/dn919648.aspx) gratuito.

3.  Quando o segundo usuário da mesma organização solicita uma assinatura do RMS para indivíduos, uma nova conta de usuário é adicionada ao diretório do Azure criado anteriormente, usando a assinatura do RMS para indivíduos da organização. Este segundo usuário pode fazer tudo o que o primeiro usuário podia fazer (proteger arquivos e ler arquivos protegidos), mas esses dois usuários agora também podem colaborar com segurança e mais facilmente, porque eles podem aplicar rapidamente modelos padrão a arquivos que restringem o acesso a contas no diretório do Azure da organização.

4.  Os usuários subsequentes da mesma organização seguem o mesmo padrão, adicionando contas de usuário (quando novos usuários se inscreverem) ao diretório Azure da organização. Quanto mais contas forem adicionadas ao diretório, mais os usuários podem colaborar de forma segura com os colegas e parceiros, e fica mais fácil evitar que pessoas não autorizadas leiam seus arquivos quando nem deveriam acessá-los.

Durante todo este processo, não há custos para a organização e nenhum trabalho é exigido do departamento de TI. No entanto, o departamento de TI pode optar por uma das seguintes opções:

-   **Gerenciar as contas e o processo de inscrição**: os administradores de TI podem assumir a propriedade do diretório e contas criados automaticamente no Azure. Eles podem gerenciar as contas através da implementação de soluções de integração de diretório, como a sincronização de senhas e logon único. Ou eles podem impedir que os usuários criem contas ou se inscrevam no RMS para pessoas físicas.

    Para obter mais informações, consulte a seguinte seção, [Como os administradores podem controlar as contas criadas para o RMS para pessoas físicas](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts).

-   **Gerenciar o Rights Management**: os administradores de TI podem converter a assinatura do RMS para indivíduos da organização para uma assinatura paga que inclui o Azure Rights Management. Ao fazer isso, o diretório do Azure e as contas existentes serão preservados para proporcionar uma transição suave para os usuários existentes que estavam usando o RMS para indivíduos. Todos os arquivos protegidos anteriormente ainda serão protegidos com as mesmas políticas e as pessoas a quem concederam permissões para usar os arquivos ainda poderão usar os arquivos da mesma forma.

    Quando você faz isso, sua organização se beneficia da capacidade de integrar o Rights Management em seus fluxos de trabalho, serviços e armazenamento de dados. Além disso, agora você pode gerenciar o Rights Management, porque você tem controle sobre a chave do locatário da organização para o Azure Rights Management. Agora você pode fazer o seguinte:

    -   Configure o Exchange e o SharePoint para dar suporte ao Azure Rights Management, ainda que eles estejam em execução no local. O Exchange e o SharePoint têm suporte nativo para os serviços online e são suportados por um conector para os servidores locais. Para obter mais informações, consulte o seguinte:

        -   As seções do Exchange Online e do SharePoint Online do [Office 365: Configuração para clientes e serviços online](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365) no tópico [Configurando aplicativos do Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)

        -   [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)

    -   Execute o e-discovery em dados de propriedade da empresa para que, se necessário, você possa descriptografar arquivos que foram protegidos com o Rights Management. Para obter mais informações, consulte [Configurando os superusuários para o Azure Rights Management e os Serviços de Descoberta ou a Recuperação de Dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

    -   Registre todas as atividades no Rights Management como é feito na sua organização. Isso é muito eficiente, porque não só é possível monitorar quais arquivos estão sendo protegidos e quem os está acessando com sucesso, mas você também pode identificar comportamentos potencialmente suspeitos de pessoas não autorizadas que estão tentando acessar os arquivos protegidos. Para obter mais informações, consulte [Registrando em log e analisando o uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

    -   Forneça aos usuários a capacidade de rastrear e revogar seus documentos protegidos, se esses recursos forem compatíveis com a sua [assinatura do Azure RMS](https://technet.microsoft.com/dn858608). Para obter mais informações, consulte [Rastrear e revogar seus arquivos](https://technet.microsoft.com/library/dn986611.aspx) no [guia de usuário do aplicativo RMS sharing](https://technet.microsoft.com/library/dn339006.aspx).

    -   Implemente a solução BYOK (Bring Your Own Key ou Traga Sua Própria Chave) para que sua chave de locatário para o Azure Rights Management seja gerada no local, de acordo com suas políticas de TI, e transferida com segurança para a Microsoft usando um Hardware Security Module (HSM). Para obter mais informações, consulte [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## <a name="BKMK_TakeControlofAccounts"></a>Como os administradores podem controlar as contas criadas para o RMS para pessoas físicas
Se você não deseja converter o RMS de assinatura para pessoas físicas da sua organização em uma assinatura paga, você ainda pode controlar as contas de usuário no diretório do Azure que foi criado para a sua organização das seguintes maneiras:

-   Implemente soluções de integração de diretório para o Azure Active Directory e sua infraestrutura de Serviços de Domínio do Active Directory. É possível sincronizar contas e senhas para que os usuários não precisem criar novas contas para usar o Rights Management, e suas políticas de senha no local serão aplicáveis ​​às novas contas de usuário do Azure. Também é possível sincronizar senhas para que os usuários não precisem se lembrar de uma senha diferente para usar o Rights Management.

-   Você pode impedir que os usuários se inscrevam para usar o Azure Rights Management com a assinatura do RMS para pessoas físicas. Na maioria dos casos, há pouca vantagem em fazer isso, porque os usuários compartilharão arquivos sem proteção (o que poderia colocar sua empresa em risco) ou usarão outro mecanismo de proteção de arquivos que não dá ao departamento de TI a opção de acessar os dados. No entanto, se você quiser impedir que usuários se inscrevam para usar o RMS para pessoas físicas, efetue uma das ações a seguir após assumir a propriedade do diretório da sua organização no Azure:

    -   Impedir todos os usuários de obterem assinaturas de autoatendimento, que inclui o RMS para pessoas físicas.  No momento, não é possível definir isto por serviço; a configuração se aplica a todas as assinaturas do Azure que usam o processo de autoatendimento. Para fazer isso, defina o parâmetro **AllowAdHocSubscriptions** como falso com o cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) do módulo do Windows PowerShell para o Active Directory do Azure. Por exemplo: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Impedir os usuários de criarem uma nova conta no Azure, o que significa que somente os usuários que já têm uma conta no Azure podem obter assinaturas de autoatendimento, que inclui o RMS para pessoas físicas.  Para fazer isso, defina o parâmetro **AllowEmailVerifiedUsers** como falso com o cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) do módulo do Windows PowerShell para o Active Directory do Azure. Por exemplo: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Sincronize sua infraestrutura de serviços de domínio do Active Directory com o Active Directory do Azure. Essa ação impede que novas contas sejam criadas quando os usuários obtêm assinaturas de autoatendimento, como o RMS para pessoas físicas, e você pode excluir ou desativar contas que foram criadas anteriormente no diretório do Azure.

Para controlar as contas de usuário no diretório do Azure ou para impedir que os usuários se inscrevam no RMS para indivíduos, você deve ter uma assinatura do Azure e possuir o diretório. Se você ainda não tiver uma assinatura do Azure, você poderá obtê-la sem custos adicionais. Se um diretório foi criado automaticamente para você durante o processo de autoatendimento, aproprie-se do domínio que foi usado para criá-lo. Se você já possui um diretório no Azure, mas os usuários especificaram um novo domínio que você usa em sua organização, mescle esse domínio em seu diretório existente. Para obter mais informações, consulte as instruções em [O que é a inscrição de autoatendimento para o Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)

## <a name="BKMK_Detect"></a>Como saber se os usuários se inscreveram para o RMS para pessoas físicas
Como administrador, como você sabe se os usuários se inscreveram para o RMS para pessoas físicas? Você pode usar qualquer um dos seguintes métodos ou uma combinação deles:

-   Pergunte aos usuários como eles protegem arquivos altamente confidenciais, especialmente quando colaboram com pessoas de fora da organização.

-   Se você tiver uma assinatura do Azure para sua organização, use o cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) para ver se **RIGHTSMANAGEMENT_ADHOC** é retornado como uma das assinaturas. Se for, essa é a assinatura do RMS para pessoas físicas que foi concedida para a empresa, com um pool de unidades ativas disponível para os usuários usarem o processo de inscrição de autoatendimento.

-   Use uma solução de gerenciamento do sistema, como o System Center Configuration Manager, para o software de inventário instalado e o software em uso. O aplicativo de compartilhamento Rights Management é executado usando o programa **ipviewer.exe** e você pode[Baixar e instalar o aplicativo](http://go.microsoft.com/fwlink/?LinkId=303970) gratuitamente para identificar outras características desse aplicativo que é usado para o inventário de software.

-   Esteja atento às extensões de nome de arquivo que criadas pelo aplicativo de compartilhamento Rights Management. As extensões de nome de arquivo .pfile e .ppdf são os exemplos mais óbvios, mas há outros arquivos que alteram sua extensão de nome de arquivo quando são protegidos nativamente pelo Rights Management. Para obter mais informações, consulte a seção [Tipos de arquivo e extensões de nome de arquivo com suporte](http://technet.microsoft.com/library/dn339003.aspx) no [guia de administrador do aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

## Consulte também
[Introdução ao Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

