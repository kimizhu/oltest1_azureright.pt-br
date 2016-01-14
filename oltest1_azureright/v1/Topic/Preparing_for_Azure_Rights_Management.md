---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Preparando o Azure Rights Management
Depois que você se inscreveu para uma assinatura na nuvem e estabeleceu uma conta para sua organização do [!INCLUDE[o365_1](../Token/o365_1_md.md)] ou do Azure Active Directory, você está pronto para habilitar o serviço do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

No entanto, antes de fazê-lo, certifique-se de que o seguinte esteja em vigor:

-   Contas de usuário e grupos na nuvem que você cria manualmente ou que são criados e sincronizados automaticamente a partir dos Serviços de Domínio do Active Directory (AD DS).

    Quando você sincroniza seu grupos e contas locais, nem todos os atributos precisam ser sincronizados. Para obter uma lista dos atributos que devem ser sincronizados para o Azure RMS, consulte esta [seção do Azure RMS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) na documentação do Active Directory do Azure. Para facilitar a implantação, recomendamos que você use o [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) para conectar seu diretórios locais ao Active Directory do Azure, mas você pode usar qualquer método de sincronização de diretório que atinja o mesmo resultado.

-   Grupos habilitados para email na nuvem que você irá usar com o Rights Management. Eles podem ser grupos internos ou criados manualmente contendo usuários que usarão o Rights Management.

    Se você tiver o Exchange Online, crie e use grupos habilitados para email usando o Centro de administração do Exchange. Se você tiver o Active Directory local e estiver sincronizando ao AD do Azure AD, use grupos habilitados para email que sejam grupos de segurança ou grupos de distribuição.

## Habilitar o Rights Management
Por padrão, o[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] está desabilitado quando você se inscreve na conta do [!INCLUDE[o365_2](../Token/o365_2_md.md)] ou do Azure AD. Para habilitar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] para a sua organização, você deve ativar o serviço. Para obter mais informações, consulte [Ativando o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## Consulte também
[Configurando o Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

