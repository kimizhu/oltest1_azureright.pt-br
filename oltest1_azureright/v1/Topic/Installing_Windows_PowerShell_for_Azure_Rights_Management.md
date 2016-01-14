---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Instalando o Windows PowerShell para Azure Rights Management
Use as seguintes informações para ajudar na instalação do Windows PowerShell para o Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

Você pode usar este módulo do Windows PowerShell para administrar o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] a partir da linha de comando usando qualquer computador que tenha uma conexão com a Internet e que atenda aos pré-requisitos listados na próxima seção. O Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] oferece suporte para scripts para automação ou pode ser necessário para cenários de configuração avançada. Para obter mais informações sobre as tarefas e as configurações de administração que o módulo suporta, consulte [Administrando o Azure Rights Management usando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Pré-requisitos
Esta tabela lista os pré-requisitos para instalar e usar o Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Requisito|Mais informações|
|-------------|--------------------|
|Uma versão do Windows que oferece suporte ao [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]módulo de administração|Verifique a lista de sistemas operacionais que oferecem suporte na seção **Requisitos de Sistema** na [página de download para a Ferramenta de Administração do Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Versão mínima do Windows PowerShell: 2.0|O suporte para o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] módulo de administração foi introduzido no Windows PowerShell 2.0.<br /><br />Por padrão, a maioria dos sistemas operacionais Windows é instalada com pelo menos a versão 2.0 do Windows PowerShell. Se você precisar instalar o Windows PowerShell 2.0, consulte [Instalar o Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx).<br /><br />Dica: Você pode confirmar a versão do Windows PowerShell que você está executando digitando **$PSVersionTable** em uma sessão do Windows PowerShell.|
|Versão mínima do Microsoft .NET Framework: 4.5<br /><br />Observação: Esta versão do Microsoft .NET Framework está incluída nos sistemas operacionais mais recentes, e você só precisará realizar uma instalação manual se o sistema operacional cliente for anterior ao Windows 8.0, ou se o sistema operacional do servidor for anterior ao Windows Server 2012.|Se a versão mínima do Microsoft .NET Framework não estiver instalada, você poderá baixar o [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />A versão mínima do Microsoft .NET Framework é necessária para algumas das classes que o módulo de administração do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] utiliza.|
|Assistente 7.0 de Conexão do Microsoft Online Services|O Assistente de Conexão do Microsoft Online Services é necessário para a [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] autenticação.<br /><br />Para obter mais informações, consulte o [Centro de Download: Assistente do Microsoft Online Services para profissionais de TI RTW](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Como instalar o módulo de administração do Rights Management

1.  Vá para o Centro de Download Microsoft e [Baixe a Ferramenta de Administração do Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721)que contém o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] módulo de administração do Windows PowerShell.

2.  Na pasta local onde você baixou e salvou o arquivo de instalação do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], clique duas vezes no arquivo executável que baixou para a plataforma (WindowsAzureADRightsManagementAdministration_x64 ou WindowsAzureADRightsManagementAdministration_x86.exe) para iniciar o Assistente de configuração de administração de gerenciamento de direitos do AD do Azure.

3.  Encerre o assistente.

O Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] agora está instalado.

## Próximas etapas
Para ver quais cmdlets estão disponíveis, inicie o Windows PowerShell com a opção **Executar como administrador** e digite o seguinte:

```
Get-Command -Module aadrm
```
Use o comando `the Get-Help <cmdlet_name>` para ver a Ajuda de um cmdlet específico.

Para obter mais informações:

-   Lista completa de cmdlets disponíveis: [Cmdlets do Azure Rights Management](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Lista dos principais cenários de configuração que dão suporte ao Windows PowerShell: [Administrando o Azure Rights Management usando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Antes de executar qualquer comando que configure o serviço [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], você deve conectar-se ao serviço usando o cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx). Quando você terminar de executar os comandos de configuração que deseja, desconecte-se do serviço usando o cmdlet [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx).

> [!NOTE]
> Se o [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] ainda não estiver ativado, você pode fazer isso depois de se conectar ao serviço usando o cmdlet [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx).

## Consulte também
[Administrando o Azure Rights Management usando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

