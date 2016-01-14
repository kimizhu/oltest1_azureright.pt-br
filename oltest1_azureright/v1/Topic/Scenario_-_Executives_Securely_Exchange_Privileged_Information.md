---
description: na
keywords: na
title: Scenario - Executives Securely Exchange Privileged Information
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
---
# Cen&#225;rio - Executivos trocam informa&#231;&#245;es privilegiadas de maneira segura
Esta seção contém as instruções do administrador e diretrizes para instruções para o usuário.Você deve concluir as instruções para administradores antes de informar os usuários sobre essa configuração.

## Instruções para administradores
![](../Image/AzRMS_AdminBanner.png)

Use estas instruções para que os executivos possam trocar emails e anexos por email entre si com segurança e para que políticas restrinjam automaticamente o acesso para os executivos sem exigir ações especiais da parte deles.Os emails e anexos serão protegidos pelo Azure Rights Management.

As instruções são adequadas para o seguinte conjunto de circunstâncias:

-   Os executivos compartilham entre si informações confidenciais que não devem ser compartilhadas com outras pessoas.

-   Os executivos não precisam fazer algo diferente ao enviar esses emails, exceto enviá-los a um endereço de email de trabalho em vez de um endereço de email pessoal.

## Requisitos para este cenário
Para que as instruções para esse cenário funcionem, deve ser feito o seguinte:

|Verificar|Requisito|Se você precisa de mais informações|
|-------------|-------------|---------------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Você preparou as contas e os grupos para o Office 365 ou o Active Directory do Azure:<br /><br />-   Um grupo habilitado para email chamado **Executivos**<br />-   Todos os executivos são membros do grupo **Executivos**|[Preparando o Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Sua chave de locatário do Azure Rights Management é gerenciada pela Microsoft. Você não está usando BYOK|[Planejando e implementando sua chave de locatário do Azure Rights Management](https://technet.microsoft.com/library/dn440580.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|O Azure Rights Management está ativado|[Ativando o Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|O Exchange Online está habilitado para o Azure Rights Management|Expanda o [Exchange Online:](https://technet.microsoft.com/library/jj585031.aspx) em [Configurando aplicativos para o Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx).|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Você configurou um modelo personalizado conforme descrito a seguir|[Configurando modelos personalizados do Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Você configurou uma regra de proteção de transporte para IRM, conforme descrito a seguir|[Criar uma Regra de proteção de transporte](https://technet.microsoft.com/library/dd302432.aspx)|

#### Para configurar o modelo personalizado para emails de executivos:

1.  No portal do Azure: Crie um novo modelo personalizado para o Azure Rights Management, contendo estes valores e configurações:

    -   Nome: **Executivos**

    -   Direitos:  Conceda ao grupo habilitado para email Executivos direitos de **Coproprietário**

2.  Publique o novo modelo.

3.  Atualize os modelos para o Exchange Online usando o comando do Windows PowerShell para Exchange Online:

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates –RMSOnline
    ```

#### Para configurar os emails de e para os executivos para serem automaticamente protegidos:

-   No centro de administração do Exchange: Crie uma nova regra de fluxo de email, contendo estes valores e configurações:

    -   Clique no ícone Novo e selecione **aplicar proteção de direitos às mensagens**

    -   Na página **nova regra**:

        -   Especifique um nome como **Aplicar os modelos Executivos a emails de executivos**

        -   Para **Aplicar esta regra se**, selecione **O remetente** ... **é um membro deste grupo** e selecione **Executivos**.

        -   Clique em **adicionar condição**, selecione **O destinatário** ... **é um membro deste grupo** e selecione **Executivos**.

        -   Para **Fazer o seguinte**, verifique se **Aplicar proteção de direitos à mensagem com** está selecionado e clique em **Selecionar um** para selecionar o modelo **Executivos**.

        -   Verifique se **Escolher um modo para esta regra**, **Impor** está selecionado.

        -   Clique em **Salvar**.

## Instruções para o usuário
Não há instruções específicas para dar aos usuários para este cenário porque a proteção de emails de e para os executivos não requer nenhuma ação especial da parte deles.As mensagens de email e os anexos são protegidos automaticamente. Assim, apenas os membros do grupo Executivos podem acessá-los.No entanto, talvez seja necessário informar aos executivos e a seu suporte técnico que os emails serão automaticamente protegidos e como isso pode restringir o uso dos emails.Por exemplo, eles não poderão ser lidos com êxito por outras pessoas se os emails ou os anexos forem encaminhados mais tarde para outros destinatários.

O exemplo a seguir pode ser enviado como uma comunicação de email padrão aos executivos, depois que o Exchange Online for configurado para esse cenário.

### Documentação do usuário de exemplo
![](../Image/AzRMS_ExampleBanner.png)

##### Anúncio de TI: Os emails de executivos agora são protegidos automaticamente

-   De agora em diante, sempre que você enviar emails a outro executivo da empresa, o conteúdo dos emails e os anexos serão automaticamente protegidos para que apenas outro executivo da empresa possa acessá-los para ler as informações, imprimi-los, copiá-los e assim por diante.Essa restrição se aplica mesmo se você encaminhar a mensagem de email a outras pessoas ou salvar os anexos.Essa proteção ajuda a impedir a perda de dados para informações confidenciais ou sigilosas.

    Observe que, se quiser que outras pessoas possam ler e editar as informações nesses emails, você deverá enviá-los por email separadamente.

    Ao enviar informações confidenciais da empresa a outro executivo, lembre-se de enviá-las a seu endereço de email de trabalho, não a um endereço de email pessoal.

**Precisa de ajuda?**

-   Contate o suporte técnico: helpdesk@vanarsdelltd.com

