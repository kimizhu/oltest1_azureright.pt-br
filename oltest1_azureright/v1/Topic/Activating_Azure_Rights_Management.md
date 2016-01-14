---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Ativando o Azure Rights Management
Quando você ativa o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), sua organização pode começar a proteger dados importantes por meio de aplicativos e serviços que oferecem suporte a essa solução de proteção de informações. Os administradores também podem gerenciar e monitorar arquivos protegidos e emails que sua organização possui. Você deve ativar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] antes que possa começar a usar os recursos de Gerenciamento de Direitos de Informação (IRM) no Office, SharePoint e Exchange, e proteger qualquer arquivo sensível ou confidencial.

Se você quiser saber mais sobre o Rights Management do Azure antes de ativar o serviço—por exemplo, quais problemas de negócios ele resolve, alguns casos típicos de uso e como funciona—consulte [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Antes de ativar[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]verifique se a sua organização tem um plano de serviço que inclui os serviços do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Caso contrário, você não poderá ativar o Azure RMS.
> 
> Para obter mais informações, consulte a seção [Assinaturas de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)no tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

Depois de ter ativado o Azure RMS, todos os usuários em sua organização podem aplicar proteção de informações aos seus arquivos e todos os usuários podem abrir (consumir) os arquivos que foram protegidos pelo Azure RMS. No entanto, se você preferir, pode restringir quem pode aplicar proteção de informações por meio de controles de integração para uma implantação em fases. Para obter mais informações, consulte a seção [Configurando controles de integração para uma implantação em fases](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) neste tópico.

## Ativando o Rights Management
Use um dos seguintes procedimentos para ativar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> Você também pode usar o cmdlet do Windows PowerShell, [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx) para ativar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Para ativar o Rights Management do centro de administração do Office 365

1.  Após inscrever-se em um plano do Office 365 que inclui o Rights Management, [entre no Office 365 com sua conta de trabalho ou escolar](https://portal.office.com/) que é um administrador para a implantação do Office 365.

2.  Se o Office 365 admin center não é exibido automaticamente, selecione o ícone do aplicativo iniciador no canto superior esquerdo e escolha**Admin**. O bloco do **Admin** é exibido apenas aos administradores do Office 365.

    > [!TIP]
    > Para obter ajuda do centro de administração, consulte[sobre o Centro de administração do Office 365 - Ajuda para Administradores](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  No painel esquerdo, expanda **CONFIGURAÇÕES DE SERVIÇO**.

4.  Clique em **Rights Management**.

    > [!NOTE]
    > Se você não consegue ver esta opção, talvez seja porque o seu plano de serviço ou sua versão do produto não suportam o Rights Management, ou ele ainda não foi atualizado para suportar o Rights Management.
    > 
    > Use as informações da seção [Assinaturas de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) do tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) para confirmar o suporte. Se o seu plano de serviço ou sua versão de produto for suportado, mas você não consegue ver a opção do Rights Management, pode ser porque o serviço ainda não esteja atualizado. Para obter ajuda com esse problema, envie uma mensagem de email para [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  No**RIGHTS MANAGEMENT**clique em**Gerenciar**.

6.  Na página de **gerenciamento de direitos**clique em**ativar**.

7.  Quando solicitado **Você deseja ativar o Rights Management?**clique em **ativar**.

Agora você deve ver **O Rights Management está ativado** e a opção para desativar.

#### Para ativar o Rights Management no Portal clássico do Azure

1.  Após você ter se inscrito na sua conta do Azure, [entre no Portal clássico do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  No painel esquerdo, clique em**ACTIVE DIRECTORY**.

3.  Na página **active directory**, clique em **RIGHTS MANAGEMENT**.

4.  Selecione o diretório a gerenciar para [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], clique em**ATIVAR** e confirme sua ação.

    > [!NOTE]
    > Se você vir um erro de ativação, pode ser porque seu plano de serviço ou versão do produto não pode oferecer suporte ao [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Use as informações da seção [Assinaturas de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) do tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) para confirmar o suporte do RMS. Para obter ajuda com esse problema, envie uma mensagem de email para [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

O **STATUS do RIGHTS MANAGEMENT** agora deve exibir**Ativo** e a opção **ATIVAR** é substituída por**DESATIVAR**.

### Valores e descrições de status do Rights Management no Portal clássico do Azure
Além do status **ATIVO**, que indica que o serviço de gerenciamento de direitos está habilitado e pronto para uso, você também poderá ver**Inativo**, **Indisponível**, ou **Não Autorizado**.

|Valor do status|Descrição|
|-------------------|-------------|
|**Ativo**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] está habilitado e pronto para usar.|
|**Inativa**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] está desabilitado e deve ser ativado antes de sua organização proteger os arquivos.|
|**Não disponível**|O [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] serviço está inativo. Tente novamente mais tarde.|
|**Não-autorizado**|Você não tem permissões para exibir o status do serviço do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Por exemplo, sua conta está bloqueada ou você não é o administrador global do locatário selecionado.|

## <a name="BKMK_OnboardingControls"></a>Configurando controles de integração para uma implantação em fases
Se você não deseja que todos os usuários consigam proteger os arquivos imediatamente usando o Azure RMS, poderá configurar os controles de integração usando o comando Windows PowerShell [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx). Você pode executar esse comando antes ou depois de ativar o Azure RMS.

> [!IMPORTANT]
> Para usar esse comando, você deve ter pelo menos a versão **2.1.0.0** do módulo [RMS Windows PowerShell do Azure](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Para verificar a versão instalada, execute: **(Get-Module aadrm –ListAvailable).Version**

Por exemplo, se você deseja inicialmente que os administradores no grupo “Departamento de TI” (que tem uma ID de objeto de fbb99ded-32a0-45f1-b038-38b519009503) consigam proteger o conteúdo para fins de teste, use o seguinte comando:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Observe que para essa opção de configuração, você deve especificar um grupo; você não pode especificar os usuários individuais.

Ou, se você quiser garantir que apenas os usuários que estão corretamente licenciados para usar o Azure RMS podem proteger o conteúdo:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Quando você usa esses controles de integração, todos os usuários da organização sempre podem consumir o conteúdo protegido que tenha sido protegido por seu subconjunto de usuários, mas eles não conseguirão aplicar a proteção de informações sozinhos a partir de aplicativos cliente. Por exemplo, eles não verão em seus clientes Office os modelos padrão que são publicados automaticamente quando o Azure RMS é ativado ou modelos personalizados que você possa configurar.  Aplicativos do lado do servidor, como o Exchange, podem implementar seus próprios controles de usuário para integração do RMS para obter o mesmo resultado.

## Próximas etapas
Agora que você ativou o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para sua organização, use o [Roteiro de implantação do Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) para verificar se existem outras etapas de configuração que você possa precisar executar antes de implementar o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] para os usuários e administradores. Por exemplo, você talvez queira usar [modelos personalizados](http://technet.microsoft.com/library/dn642472.aspx) para facilitar para que os usuários apliquem a proteção de informações em arquivos, conectem os servidores locais para usar[!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] a instalação do [conector RMS](http://technet.microsoft.com/library/dn375964.aspx)e implantar o[aplicativo de compartilhamento Rights Management](http://technet.microsoft.com/library/jj585031.aspx)que dá suporte à proteção de todos os tipos de arquivos em todos os dispositivos. Serviços do Office, como o Exchange Online e o SharePoint Online exigem configuração adicional antes de poder usar os recursos de gerenciamento de direitos de informação (IRM). Se não houver outras etapas de configuração que você precise executar, consulte [Usando o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) para obter orientação operacional para dar suporte a uma implantação bem-sucedida para sua organização.

Para obter informações sobre como os aplicativos funcionam com [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], consulte [Como os aplicativos dão suporte ao Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Consulte também
[Configurando o Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

