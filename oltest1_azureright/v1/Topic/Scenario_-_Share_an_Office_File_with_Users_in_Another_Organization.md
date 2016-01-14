---
description: na
keywords: na
title: Scenario - Share an Office File with Users in Another Organization
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc
---
# Cen&#225;rio: compartilhando um arquivo do Office com usu&#225;rios com outra organiza&#231;&#227;o
Esta seção contém as instruções do administrador, um modelo para obter instruções de usuário e um exemplo de como as instruções do usuário final podem parecer.Antes de fornecer a documentação do usuário final para seus usuários, você deve concluir as instruções para administradores.

## Instruções para administradores
![](../Image/AzRMS_AdminBanner.png)

Use estas instruções e o modelo a seguir para criar suas próprias instruções do usuário final para ajudar os usuários a enviar por email um arquivo do Office com segurança para pessoas em outra organização.Por exemplo, o arquivo do Office pode ser um documento do Word, planilha do Excel ou apresentação do PowerPoint que contenha informações da lista de preços para um parceiro, uma lista de produtos para um revendedor ou uma lista de linhas de tempo de entrega com clientes em potencial.Quando os usuários seguirem as instruções, o arquivo anexado à mensagem de email estará protegido pelo Azure Rights Management.

As instruções são adequadas para o seguinte conjunto de circunstâncias:

-   O funcionário tem que enviar informações de fora da organização, na forma de um documento do Office.

-   O documento contém informações que não são públicas, mas não são exclusivamente para uso interno.

-   Os usuários do destinatário não tem um requisito para compartilhar essas informações com outras pessoas, imprimi-la ou usá-la como parte de sua própria documentação.Se esse não for o caso, você pode alterar as instruções do usuário de selecionar permissões de somente exibição para outra opção que permita que o destinatário altere o anexo.

-   O funcionário está interessado em saber quando este documento for aberto pelo usuário externo.

Nas instruções de usuário a seguir, substitua *&lt; nome do tipo de documento do Office &gt;* com o tipo de documento que seus usuários estarão enviando.Use palavras específicas e conhecidas para seus fluxos de trabalho, como “lista de preços”, “tempo de entrega”, e “proposta de oferta” em vez de “Documento do Word” e “Planilha do Excel”.Substitua também *&lt; detalhes de contato &gt;* com instruções sobre como os usuários podem entrar em contato com o suporte técnico, como um link de site, endereço de email ou número de telefone.

Em seguida, faça modificações adicionais que você deseja para as instruções e forneça essas instruções aos usuários.Por exemplo, adicione o documento em um site do SharePoint ou os envie por email.

Modificações que você pode querer fazer nas instruções:

-   Na etapa 2, sugerimos **Viewer - View Only** para as permissões, que torna o documento anexado (mas não o original) somente leitura para os destinatários.Se essa restrição não for adequada para suas necessidades de negócios, altere essa opção para outro conjunto de permissões, como **Reviewer - View and Edit**.

-   Na etapa 3, sugerimos **Permitir que eu revogue o acesso a esses documentos imediatamente** para que não exista nenhum atraso se os seus usuários revogarem o documento mais tarde, mas a definição desta opção requer que o destinatário sempre tenha uma conexão com a Internet para abrir o anexo.Esta etapa também requer que você tenha uma assinatura que ofereça suporte ao controle de documentos e revogação.Exclua esta etapa se ela não for adequada para seus usuários.

-   Na etapa 4, sugerimos a opção **Envie-me um email quando alguém tentar abrir este documento**.Se os usuários controlarem seus documentos usando o portal de controle de documento, você pode decidir que a notificação por email não é necessária e excluir esta etapa.

-   As etapas não incluem a definição de uma data de expiração.Se o anexo for sensível ao tempo, adicione outra etapa para definir um tempo de expiração apropriado, como 90 dias a partir do envio da mensagem de email.

> [!NOTE]
> Para obter mais informações sobre cada uma das opções que os usuários podem selecionar, consulte [Opções da caixa de diálogo para o aplicativo de compartilhamento do Rights Management](https://technet.microsoft.com/library/dn574738.aspx)

## Requisitos para este cenário
Para ver as instruções de usuário para este cenário funcionarem, os seguintes requisitos devem estar em vigor:

|Verificar|Requisito|Se você precisar de mais informações|
|-------------|-------------|----------------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Você preparou contas e grupos do Office 365 ou o Azure Active Directory|[Preparando o Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|O Azure Rights Management está ativado|[Ativando o Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|O aplicativo de compartilhamento do Rights Management é implantado nos computadores dos usuários que executam o Windows|[Implantação automática para o aplicativo de compartilhamento Microsoft Rights Management](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Os usuários têm o Outlook do Office 2013|Se os usuários têm o Office 2010, substitua a captura de tela por uma versão equivalente para que a imagem corresponda a que os usuários veem.|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Sua assinatura do Azure RMS inclui rastreamento de documento|Se sua assinatura do Azure RMS não inclui controle de documento e revogação, os usuários não poderão concluir todas as etapas nas instruções do usuário.Nesse caso, adquira também uma assinatura que ofereça suporte a esses recursos ou modifique as instruções do usuário para remover as etapas que usam esses recursos.<br /><br />Para verificar o suporte de assinatura: [Comparação de Ofertas do Rights Management Services (RMS)](https://technet.microsoft.com/dn858608).|

## Instruções para o usuário:
Copie e cole as seguintes instruções para os usuários finais e modifique-as de acordo com as instruções do administrador para esse cenário.A documentação de exemplo mostra como este conjunto de instruções pode parecer para os usuários, após as personalizações.

![](../Image/AzRMS_UsersBanner.png)

#### Como compartilhar um &lt;nome do tipo de documento do Office&gt;

1.  Crie a mensagem de email, especificando o endereço ou endereços de email, digite sua mensagem e anexe o *&lt;nome do tipo de documento do Office&gt;* à mensagem de email.Depois, na guia **Message** no grupo do **RMS**, clique em **Compartilhamento Protegido** e clique em **Compartilhamento Protegido** novamente:

    ![](../Image/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  Na caixa de diálogo **compartilhamento protegido**, selecione **Viewer – View Only**:

    ![](../Image/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Selecione **Permitir que eu revogue o acesso a esses documentos imediatamente**.

    ![](../Image/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Selecione **Enviar-me um email quando alguém tentar abrir esses documentos**:

    ![](../Image/AzRMS_SharedProtected_EmailMe.PNG)

5.  Clique em **Enviar Agora**.

    ![](../Image/AzRMS_ShareProtected_SendNow.PNG)

Quando alguém nos campos **Para**, **Cc** ou **Cco** receber este email, eles veem uma mensagem que fornece as instruções sobre como ler o anexo *&lt;nome do tipo de documento do Office&gt;*.Eles podem ler o documento em vários dispositivos, incluindo iPads, iPhones, tablets Android e telefones, computadores Mac e computadores com Windows.

Use o [portal de controle de documento](https://track.azurerms.com/) para controlar se e quando abrirem o &lt;nome do tipo de documento do Office&gt; anexado.Considere entrar em contato com eles com uma chamada por telefone de acompanhamento logo depois que você vir que eles abriram &lt;nome do tipo de documento do Office&gt;.

**Precisa de ajuda?**

-   Para obter informações adicionais:

    -   [Proteger um arquivo que você compartilha por email](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Rastrear e revogar seus documentos](https://technet.microsoft.com/library/dn986611.aspx)

-   Entre em contato com o suporte técnico:

    -   *&lt;detalhes do contato&gt;*

### Documentação do usuário de exemplo
![](../Image/AzRMS_ExampleBanner.png)

##### Como compartilhar uma lista de preços com o cliente

1.  Crie a mensagem de email, especificando o endereço ou endereços de email do cliente, digite sua mensagem e anexe lista depreços mais recente à mensagem de email.Depois, na guia **Message** no grupo do **RMS**, clique em **Compartilhamento Protegido** e clique em **Compartilhamento Protegido** novamente:

    ![](../Image/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  Na caixa de diálogo **compartilhamento protegido**, selecione **Viewer – View Only**:

    ![](../Image/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Selecione **Permitir que eu revogue o acesso a esses documentos imediatamente**.

    ![](../Image/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Selecione **Enviar-me um email quando alguém tentar abrir esses documentos**:

    ![](../Image/AzRMS_SharedProtected_EmailMe.PNG)

5.  Clique em **Enviar Agora**.

    ![](../Image/AzRMS_ShareProtected_SendNow.PNG)

Quando alguém nos campos **Para**, **Cc** ou **Cco** receber este email, eles veem uma mensagem que fornece as instruções sobre como ler o a lista de preços anexa.Eles podem ler o documento em vários dispositivos, incluindo iPads, iPhones, tablets Android e telefones, computadores Mac e computadores com Windows.

Use o [portal de controle de documento](https://track.azurerms.com/) para controlar se e quando abrirem lista de preços anexa.Considere entrar em contato com eles com uma chamada por telefone de acompanhamento logo depois que você vir que eles abriram a lista de preços.

**Precisa de ajuda?**

-   Para obter informações adicionais:

    -   [Proteger um arquivo que você compartilha por email](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Rastrear e revogar seus documentos](https://technet.microsoft.com/library/dn986611.aspx)

-   Entre em contato com o suporte técnico:

    -   Email: helpdesk@vanarsdelltd.com

