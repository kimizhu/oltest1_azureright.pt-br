---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Roteiro de implanta&#231;&#227;o do Azure Rights Management
Use as seguintes etapas para se preparar para implementar e gerenciar o Azure Rights Management (Azure RMS) para a sua organização.

No entanto, se quiser testar rapidamente o Azure RMS para si mesmo, em vez de distribuí-lo em um ambiente de produção, consulte [Tutorial de início rápido para o gerenciamento de direitos Azure](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Antes de realizar estas etapas, certifique-se de ter revisado o [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Etapa 1: Confirme se você tem uma assinatura que inclui o Azure Rights Management
Há mais de um tipo de assinatura que inclui [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Consulte a seção [Assinaturas de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) no tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) e verifique se sua assinatura inclui a funcionalidade que você deseja usar em sua organização fazendo referência à tabela em [Ofertas de comparação do Rights Management Services (RMS)](https://technet.microsoft.com/dn858608).

## Etapa 2: Prepare a sua conta de locatário para usar o Rights Management
Antes de começar a usar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], prepare-se:

1.  Certifique-se de que seu locatário do Azure ou Office 365 contém as contas de usuário e grupos que serão usados pelo Azure RMS para autenticar usuários de sua organização. Se necessário, crie essas contas e grupos ou sincronize-as à partir do seu diretório local. Para obter mais informações, consulte [Preparando o Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Decida se deseja que a Microsoft gerencie sua chave de locatário (a padrão), ou se quer gerar e gerenciar sua chave de locatário por conta própria (conhecido como trazer a sua própria chave, ou BYOK). Observe que, no momento, você não pode usar o BYOK se usar o Exchange Online. Para obter mais informações, consulte [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Instale o módulo do Windows PowerShell do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] em pelo menos um computador que tenha acesso à Internet. Você pode executar esta etapa agora ou mais tarde. Para obter mais informações, consulte [Instalando o Windows PowerShell para Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Se você estiver usando serviços do Rights Management no local: Execute uma migração para mover as chaves, modelos e URLs para a nuvem. Para obter mais informações, consulte [Migrando do AD RMS para o Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Ative o Rights Management de modo que você possa começar a usar o serviço. Se uma implantação em fases for necessária, configure controles de integração de usuário para restringir o uso a usuários específicos. Para obter mais informações, consulte [Ativando o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

Opcionalmente, considere a configuração a seguir:

-   Personalize modelos se os modelos de política de direitos padrão não forem suficientes para a sua organização. Você pode executar esta etapa agora ou mais tarde. Para obter mais informações, consulte [Configurando modelos personalizados do Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Log de uso para que você possa monitorar como a sua organização está usando o Rights Management. Você pode executar esta etapa agora ou mais tarde. Para obter mais informações, consulte [Registrando em log e analisando o uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Etapa 3: Configure os seus aplicativos e serviços para o Rights Management
A configuração dos seus aplicativos pode incluir a instalação do aplicativo de compartilhamento Rights Management e ativar o suporte para os recursos de IRM (Gerenciamento de Direitos de Informação) no Exchange Online ou no SharePoint Online. Para obter mais informações, consulte [Configurando aplicativos do Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Se você tiver serviços de TI existentes que precisam de inspecionar os arquivos que o Azure RMS protegerá — como soluções de prevenção de vazamento de dados (DLP), os gateways de criptografia de conteúdo (CEG) e produtos antimalware — configure as contas de serviço que serão superusuários para o Azure RMS. Para obter mais informações, consulte [Configurando os superusuários para o Azure Rights Management e os Serviços de Descoberta ou a Recuperação de Dados](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Se você tiver serviços no local que deseja usar com o Azure Rights Management, instale e configure o conector Rights Management. Para obter mais informações, consulte [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Etapa 4: Publique e consuma conteúdo com direitos protegidos
Você agora está pronto para publicar e consumir conteúdo protegido e registrar como a sua empresa está usando o gerenciamento de direitos. Para obter mais informações, consulte [Usando o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Etapa 5: Administre o Rights Management para sua conta de locatário, conforme necessário
Ao começar a usar o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], talvez você ache que o módulo do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] para Windows PowerShell seja útil para ajudar na criação de scripts ou a automatizar alterações administrativas. Para obter mais informações, consulte [Administrando o Azure Rights Management usando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Consulte também
[Configurando o Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

