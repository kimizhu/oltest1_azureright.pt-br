---
description: na
keywords: na
title: Scenario - Retain Control of Documents Stored in SharePoint
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
---
# Cen&#225;rio - Mantendo o controle de documentos armazenados no SharePoint
Esta seção contém as instruções do administrador e diretrizes para instruções para o usuário.Você deve concluir as instruções para administradores antes de informar os usuários sobre essa configuração.

## Instruções para administradores
![](../Image/AzRMS_AdminBanner.png)

Use estas instruções para garantir que os documentos do Office armazenados no SharePoint permaneçam sob seu controle usando bibliotecas protegidas.Por exemplo, os documentos são protegidos automaticamente contra vazamento acidental ou pretendido pelos usuários, e você pode bloquear o acesso ao conteúdo mesmo depois que ele é baixado ou sincronizado.Os arquivos que você deseja proteger podem ser para colaboração em planos ou documentos de design ou para entregas.Quando você configurar bibliotecas protegidas para o SharePoint, os arquivos do Office armazenados nelas estarão protegidos pelo Azure Rights Management.

As instruções são adequadas para o seguinte conjunto de circunstâncias:

-   Os funcionários compartilham e colaboram usando documentos do Office.

-   Os documentos contêm informações que não são públicas, mas não necessariamente apenas para uso interno.

-   Os funcionários não precisam definir ou alterar as permissões que um administrador define no nível de biblioteca.

## Requisitos para este cenário
Para que este cenário funcione, o seguinte deve ser feito:

|Verificar|Requisito|Se você precisa de mais informações|
|-------------|-------------|---------------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Você preparou contas e grupos do Office 365 ou do Active Directory do Azure|[Preparando o Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|O Azure Rights Management está ativado|[Ativando o Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Se você pretende usar o SharePoint Server: Implante o conector RMS e configure-o para o SharePoint|[Implantando o conector do Azure Rights Management](https://technet.microsoft.com/library/dn375964.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Configurar o SharePoint para o IRM e bibliotecas protegidas|[Configurar o Gerenciamento de Direitos de Informação (IRM) no centro de administração do SharePoint](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[Aplicar o Gerenciamento de Direitos de Informação a uma lista ou biblioteca](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

## Instruções para o usuário
Não há instruções específicas para dar aos usuários para esse cenário porque as bibliotecas protegidas não exigem ações especiais dos usuários.Os documentos são automaticamente protegidos, de acordo com as permissões que um administrador do SharePoint define para o site.No entanto, talvez seja necessário informar aos usuários e a seu suporte técnico quais bibliotecas são protegidas e como isso pode restringir o uso dos documentos.Por exemplo, devido a limitações atuais, os documentos podem ser exibidos, mas não editados com dispositivos móveis.

O exemplo a seguir pode ser enviado como uma comunicação de email padrão ao departamento ou equipe relevante, depois que uma biblioteca do SharePoint é configurada para usar o Azure RMS.

### Documentação do usuário de exemplo
![](../Image/AzRMS_ExampleBanner.png)

##### Anúncio de TI: Alterações no site de Relatórios e Previsões de Vendas

-   O site do SharePoint, **Relatórios e Previsões de Vendas**, agora está configurado para colaboração segura.De agora em diante, você deve editar as planilhas e os documentos do Word armazenados nesse site diretamente. Por exemplo, você não pode salvá-los em um local diferente para edição posterior nem enviá-los por email-los a outra pessoa.Você pode exibi-los com dispositivos móveis, mas deve usar um computador com o Windows para editá-los.

**Precisa de ajuda?**

-   Contate o suporte técnico: helpdesk@vanarsdelltd.com

