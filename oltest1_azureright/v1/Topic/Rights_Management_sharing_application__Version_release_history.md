---
description: na
keywords: na
title: Rights Management sharing application: Version release history
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
---
# Aplicativo de compartilhamento do Rights Management: hist&#243;rico de lan&#231;amento de vers&#227;o
A equipe do Rights Management atualiza o aplicativo Rights Management sharing regularmente para correções e novas funcionalidades. Use as informações a seguir para ver o que há de novo ou o que foi alterado em uma versão. A versão mais recente é listada primeiro.

As versões anteriores a 1º de janeiro de 2015 não são listadas.

> [!NOTE]
> Se você tiver um comentário ou uma pergunta sobre o aplicativo RMS sharing, envie um email para [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question).

## Version 1.0.2004.0
**Lançada**: 11/12/2015

**Correções**:

-   Melhorias para as mensagens de erro (precisão e clareza).

-   Melhorias de desempenho para criptografar e descriptografar conteúdo.

**Novos recursos**:

-   Suporte para instalação de não-administrador, para que os usuários padrão possam instalar o aplicativo RMS sharing.

    Existem algumas restrições para usuários padrão que executam o Office 2010. Para obter mais informações, consulte a seção [Se você não é um administrador local e usa o Office 2010](../Topic/Download_and_install_the_Rights_Management_sharing_application.md#BKMK_SetupOffice2010) nas instruções do usuário [Baixar e instalar o aplicativo Rights Management sharing](../Topic/Download_and_install_the_Rights_Management_sharing_application.md).

## Versão 1.0.1908.0
**Lançada**: 16/9/2015

**Correções**:

-   Suporte para Multi-Factor Authentication (MFA) para o Azure RMS, que também remove a dependência do assistente de conexão da Microsoft que usa autenticação moderna.

    Para obter mais informações, consulte a seção [Multi-Factor Authentication (MFA) e Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_MFA) em [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Versão 1.0.1784.0
**Lançada**: 30/7/2015

**Correções**:

-   O intervalo de atualização padrão para modelos de política de direitos foi reduzido de 7 dias para 1 dia.

-   Pequeno número de bugs menores e regressões.

## Versão 1.0.1770.0
**Lançada**: 25/4/2015

**Correções**:

-   Agora, somente o proprietário e os coproprietários podem remover a proteção. Co-autores não podem remover a proteção.

-   Os arquivos que estão em um compartilhamento de rede agora podem ser protegidos.

**Novos recursos**:

-   Suporte para rastreamento e revogação de documentos. Para obter mais informações, consulte [Rastreie e revogue seus documentos ao usar o aplicativo RMS sharing](../Topic/Track_and_revoke_your_documents_when_you_use_the_RMS_sharing_application.md).

-   Suporte de modelo quando você escolhe **Compartilhamento protegido**:

    -   Agora você pode selecionar modelos.

    -   Em vez do controle deslizante, você verá uma caixa de listagem que inclui modelos e permissões personalizadas.

    -   Você não verá mais opções para **Permitir consumo em todos os dispositivos** e **Impor restrições de uso**. Em vez disso, **Proteção genérica** é selecionada automaticamente, dependendo do tipo de arquivo.

    Para obter mais informações, consulte [Opções da caixa de diálogo do aplicativo de compartilhamento do Rights Management](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md).

## Versão 1.0.1667.0
**Lançada**: 19/1/2015

**Correções**:

-   Suporte a fontes do idioma chinês no visualizador PPDF do aplicativo RMS sharing.

-   Melhor manipulação de erros e mensagens.

-   Correção para um problema com a notificação de atualização automática quando uma versão mais recente do aplicativo está disponível para download.

**Novos recursos**:

-   **Suporte para vários domínios de email dentro de sua organização**: Se você usa o AD RMS e os usuários em sua organização possuem vários domínios de email, essa atualização permite que os usuários consumam conteúdo protegido por usuários em sua organização em outros domínios. Para obter mais informações, consulte a seção [Somente AD RMS: Suporte para vários domínios de email dentro de sua organização](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains) no [Guia do administrador do aplicativo de compartilhamento Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md).

