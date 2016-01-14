---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# Migrando do AD RMS para o Azure Rights Management
Use o seguinte conjunto de instruções para migrar sua implantação do Active Directory Rights Management Services (AD RMS) para o Azure Rights Management (Azure RMS). Após a migração, os usuários ainda terão acesso aos documentos e às mensagens de email que sua organização protegia usando o AD RMS, e o novo conteúdo protegido usará o Azure RMS.

Não sabe se essa migração do AD RMS é adequada para sua organização?

-   Para ver uma introdução ao Azure RMS, conhecer os problemas de negócios que ele pode solucionar, ver sua aparência para administradores e usuários e saber como funciona, consulte [O que é o Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

-   Para ver uma comparação do Azure RMS com o AD RMS, consulte [Comparando o Azure Rights Management e o AD RMS](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Pré-requisitos para migrar do AD RMS para o Azure RMS
Antes de iniciar a migração para o Azure RMS, lembre-se de seguir estes pré-requisitos e entender as limitações.

|Requisito|Mais informações|
|-------------|--------------------|
|Uma implantação do RMS com suporte|Todas as versões do AD RMS do Windows Server 2008 por meio do Windows Server 2012 R2 suportam uma migração para o Azure RMS:<br /><br />-   Windows Server 2008 (x86 ou x64)<br />-   Windows Server 2008 R2 (x64)<br />-   Windows Server 2012 (x64)<br />-   Windows Server 2012 R2 (x64) **Note:** Se você estiver executando o Windows RMS no Windows Server 2003, esta versão do sistema operacional não será mais suportada durante 2015. Você pode migrar esta versão do RMS para o Azure RMS, mas esse processo só é suportado se ainda há suporte para o sistema operacional. Como alternativa, importe o seu domínio de publicação confiável (TPD) para uma versão do AD RMS compatível e, em seguida, importe novamente o TPD sem a opção de compatibilidade do RMS 1.0. Para obter mais informações sobre os TPDs, consulte [Domínio de Publicação Confiável](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Todas as topologias do AD RMS válidas têm suporte:<br /><br />-   Floresta única, cluster de RMS único<br />-   Floresta única, vários clusters de RMS somente de licenciamento<br />-   Várias florestas, vários clusters de RMS **Note:** Por padrão, vários clusters de RMS migram para um único locatário do Azure RMS. Se desejar locatários diferentes do RMS, trate-os como migrações diferentes. Uma chave de um cluster do RMS não pode ser importada para mais de um locatário do Azure RMS.|
|Todos os requisitos para executar o Azure RMS, incluindo um locatário do Azure RMS (não ativado)|Consulte [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Embora você deva ter um locatário do Azure RMS antes de migrar do AD RMS, recomendamos que não ative o serviço de Rights Management antes da migração. O processo de migração inclui essa etapa depois de exportar chaves e modelos do AD RMS e importá-los para o Azure RMS. No entanto, se o Azure RMS já está ativado, você ainda pode migrar do AD RMS.|
|Preparação para o Azure RMS:<br /><br />-   Sincronização de diretórios entre seu diretório local e o Active Directory do Azure<br />-   Grupos habilitados para email no Active Directory do Azure|Consulte [Preparando o Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).|
|Se você usou a funcionalidade de gerenciamento de direitos de informação (IRM) do Exchange Server (por exemplo, regras de transporte e o Outlook Web Access) ou o SharePoint Server com o AD RMS:<br /><br />-   Planeje por um curto período de tempo em que o IRM não estará disponível nesses servidores|Você pode continuar usando o IRM nesses servidores com o Azure RMS após a migração. Porém, uma das etapas de migração é desabilitar temporariamente o serviço IRM, instalar e configurar um conector, reconfigurar os servidores e reabilitar o IRM.<br /><br />Essa é a única interrupção no serviço durante o processo de migração.|
Limitações:

-   Embora o processo de migração suporte a migração da chave do certificado de licenciamento do servidor (SLC) para um módulo de segurança de hardware (HSM) para o Azure RMS, o Exchange Online não suporta essa configuração no momento. Se desejar usar todas as funcionalidades IRM com o Exchange Online após migrar do Azure RMS, a sua chave de locatário do Azure RMS deve ser [gerenciada pela Microsoft](http://technet.microsoft.com/library/dn440580.aspx). Como alternativa, você pode executar o IRM com funcionalidade reduzida no Exchange Online quando seu locatário do Azure RMS é gerenciado por você (BYOK). Para obter mais informações sobre como usar o Exchange Online com o Azure RMS, consulte [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) nessas instruções.

-   Se tiver clientes e software sem suporte com o Azure RMS, eles não poderão proteger ou consumir conteúdo protegido pelo Azure RMS. Verifique a seção de clientes e aplicativos que têm suporte no tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

-   Se você importar sua chave local para o Azure RMS como arquivada (você não define o TPD para ativo durante o processo de importação) e migrar usuários em lotes para uma migração em fases, o conteúdo protegido recentemente pelos usuários migrados não estará acessível a usuários que permanecem no AD RMS. Nesse cenário, sempre que possível, mantenha o tempo da migração curto e migre usuários em lotes lógicos de modo que se eles colaboram entre si, eles são migrados juntos.

    Essa limitação não se aplica quando você define o TPD para ativo durante o processo de importação, porque todos os usuários protegerão o conteúdo usando a mesma chave. Recomendamos essa configuração porque permite migrar todos os usuários independentemente e em seu próprio ritmo.

-   Se você colabora com parceiros externos (por exemplo, usando domínios de usuário confiáveis ou federação), eles também devem migrar para o Azure RMS, seja ao mesmo tempo que a migração ou assim que possível posteriormente. Para continuar acessando o conteúdo que a sua organização protegia anteriormente usando o AD RMS, deve-se fazer alterações na configuração do cliente que sejam semelhantes às feitas por você e incluídas neste documento.

    Devido as possíveis variações de configuração que seus parceiros possam ter, as instruções exatas para essa reconfiguração está fora do escopo deste documento. Para obter ajuda, entre em contato com Microsoft Customer Support Services (CSS).

## Etapas para migrar do AD RMS para o Azure RMS

|Etapas da migração|Mais informações|
|----------------------|--------------------|
|**1. Baixar as Ferramentas de Administração de Gerenciamento do Azure RMS**|Para obter instruções, consulte [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Exportar os dados de configuração do AD RMS e importá-los para o Azure RMS**|Exporte os dados de configuração (chavfes, modelos, URLs) do AD RMS para um arquivo XML e, em seguida, carregue esse arquivo para o Azure RMS usando o cmdlet Import-AadrmTpd do PowerShell do Windows. Dependendo da sua configuração de chave no AD RMS, poderão ser necessárias etapas adicionais:<br /><br />-   Chave protegida por software para migração de chave protegida por software: Chaves com base em senha centralmente gerenciadas no AD RMS para chave de locatário gerenciada pelo Microsoft Azure RMS. Este é o caminho de migração mais simples e não é preciso fazer mais nada.<br />-   Chave protegida por HSM para migração de chave protegida por HSM: Chaves que são armazenadas por HSM para AD RMS para chave de locatário do Azure RMS gerenciada pelo cliente (o cenário “traga a sua própria chave” ou BYOK). Isso exige etapas adicionais para transferir a chave do seu Thales HSM local para o Azure RMS HSM.<br />-   Chave protegida por software para migração de chave protegida por HSM: Chaves com base em senha gerenciadas centralmente no AD RMS para chave de locatário do Azure RMS gerenciada pelo cliente (o cenário “traga a sua própria chave” ou BYOK). Isso exige a mais alta configuração, porque você deve primeiro extrair a sua chave de software e importá-la para um HSM local e, em seguida, seguir outros procedimentos para transferir a chave do seu Thales HSM local para o Azure RMS HSM.<br /><br />Para obter instruções, consulte [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. Ativar o seu locatário do RMS**|Se possível, siga esta etapa após o processo de importação e não antes.<br /><br />Para obter mais informações e instruções, consulte [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Configurar modelos importados**|Quando você importa seus modelos de política de direitos, o seu status é arquivado. Se desejar que os usuários possam vê-los e usá-los, altere o status do modelo para publicado no Portal clássico do Azure.<br /><br />Para obter instruções, consulte [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Reconfigurar clientes para usar o Azure RMS**|Os computadores existentes com Windows devem ser reconfigurados para usar o serviço do Azure RMS, em vez do AD RMS. Essa etapa se aplica a computadores da sua organização e a computadores de organizações parceiras se você tiver colaborado com elas enquanto estava executando o AD RMS.<br /><br />Além disso, se você tiver implantado as [extensões de dispositivo móvel](http://technet.microsoft.com/library/dn673574.aspx) para oferecer suporte aos dispositivos móveis como telefones iOS e iPads, telefones e tablets Android, Windows phone e computadores Mac, você deve remover os registros SRV no DNS que redirecionaram esses clientes para usar o AD RMS.<br /><br />Para obter instruções, consulte [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. Configurar a integração do IRM com o Exchange Online**|Essa etapa será necessária se você quiser usar o Exchange Online com o Azure RMS.<br /><br />Para obter instruções, consulte [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. Implantar o conector RMS**|Esta etapa é necessária se desejar usar qualquer um dos seguintes serviços locais com o Azure RMS:<br /><br />-   Exchange Server (por exemplo, regras de transporte e Outlook Web Access)<br />-   SharePoint Server<br />-   Windows Server executando a Infraestrutura de Classificação de Arquivos<br /><br />Para obter instruções, consulte [Etapa 7. Encerrar o AD RMS](#BKMK_Step7Migration).|
|**8. Encerrar o AD RMS**|Depois de confirmar que todos os clientes estão usando o Azure RMS e não estão mais acessando os servidores do AD RMS, você pode encerrar sua implantação do AD RMS.<br /><br />Para obter instruções, consulte [Etapa 8. Criar novamente sua chave de locatário do Azure RMS](#BKMK_Step8Migration).|
|**9. Criar novamente a sua chave de locatário do Azure RMS**|Essa etapa é necessária se não estiver executando no Modo Criptográfico 2 antes da migração e é opcional mas recomendado para todas as migrações, para ajudar a proteger a segurança da chave de locatário do Azure RMS.<br /><br />Para obter instruções, consulte [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Etapa 1: Baixar a ferramenta de Administração do Azure Rights Management
Vá para a Central de Download da Microsoft e baixe a [Ferramenta de Administração do Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721), que contém o módulo de administração do Azure RMS para o Windows PowerShell.

### <a name="BKMK_Step2Migration"></a>Etapa 2. Exportar os dados de configuração do AD RMS e importá-los para o Azure RMS
Esta etapa é um processo de duas partes:

1.  Exporte os dados de configuração do AD RMS, exportando os domínios de publicação confiável (TPDs) para um arquivo .xml. Esse processo é o mesmo para todas as migrações.

2.  Importe os dados de configuração para o Azure RMS. Existem processos diferentes para essa etapa, dependendo da sua configuração atual de implantação do AD RMS e da sua topologia preferencial para a chave de locatário do Azure RMS.

#### Exportar os dados de configuração do AD RMS
Faça o seguinte em todos os clusters do AD RMS, para todos os domínios de publicação confiáveis que já protegeram o conteúdo da sua organização. Você não precisa executar isso em clusters somente de licenciamento.

> [!NOTE]
> Se você estiver usando gerenciamento de direitos do Windows Server 2003, em vez destas instruções, siga o procedimento [Exportar chave privada SLC, TUD, TPD e RMS](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) do tópico [Migrando do Windows RMS para AD RMS em uma infraestrutura diferente](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx).

###### Para exportar os dados de configuração (informações de domínio de publicação confiável)

1.  Faça logon no cluster do AD RMS como um usuário com permissões administrativas do AD RMS.

2.  No console de gerenciamento do AD RMS (**Active Directory Rights Management Services**), expanda o nome do cluster AD RMS, expanda **Diretivas de confiança**e clique em**Domínios de Publicação Confiável**.

3.  No painel de resultados, selecione o domínio de publicação confiável e, no painel de ações, clique em **Exportar Domínio de Publicação Confiável**.

4.  Na caixa de diálogo **Exportar Domínio de Publicação Confiável**:

    -   Clique em **Salvar Como**e salve o caminho e o nome de arquivo de sua escolha. Verifique se você especificou **.xml** como a extensão do nome do arquivo (ela não é acrescentada automaticamente).

    -   Especifique e confirme uma senha forte. Guarde essa senha, pois você precisará dela mais tarde, quando importar os dados de configuração para o Azure RMS.

    -   Não marque a caixa de seleção para salvar o arquivo de domínio confiável na versão 1.0 do RMS.

Quando tiver exportado todos os domínios de publicação confiáveis, você estará pronto para iniciar o procedimento para importar tais dados para o Azure RMS.

#### Importar os dados de configuração para o Azure RMS
Os procedimentos exatos para essa etapa dependem da sua configuração atual de implantação do AD RMS e da sua topologia preferencial para a chave de locatário do Azure RMS.

Sua implantação atual do AD RMS usará uma das seguintes configurações para sua chave do certificado de licenciante para servidor (SLC):

-   Proteção por senha no banco de dados do AD RMS. Essa é a configuração padrão.

-   Proteção de HSM usando um módulo de segurança de hardware (HSM) Thales.

-   Proteção de HSM usando um módulo de segurança de hardware (HSM) de um fornecedor que não seja a Thales.

-   Senha protegida usando um provedor criptográfico externo.

> [!NOTE]
> Para saber mais sobre como usar módulos de segurança de hardware com o AD RMS, consulte [Usando o AD RMS com módulos de segurança de hardware](http://technet.microsoft.com/library/jj651024.aspx).

As duas opções de topologia de chave de locatário do Azure RMS são: A Microsoft gerencia sua chave de locatário (**gerenciada pela Microsoft**) ou você pode gerenciar a sua chave de locatário (**gerenciada pelo cliente**). Quando você gerencia a sua própria chave de locatário do Azure RMS, nós chamamos isso de “traga sua própria chave” (BYOK) e requer um módulo de segurança de hardware (HSM) da Thales. Para obter mais informações, consulte a seção [Escolha sua topologia de chave de locatário: Gerenciada pela Microsoft (o padrão) ou gerenciada por você (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey)no tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

> [!IMPORTANT]
> Atualmente o Exchange Online não é compatível com Azure RMS BYOK.  Se você quiser usar o BYOK após a migração e planeja usar o Exchange Online, certifique-se de que você compreende como essa configuração reduz a funcionalidade do IRM para o Exchange Online. Revise as informações na seção [Preços e restrições do BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) do tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) para ajudá-lo a escolher o melhor topologia de chave do locatário do Azure RMS para a migração.

Use a tabela a seguir para identificar o procedimento a ser usado para a migração. Não há suporte para combinações que não estão listadas.

|Implantação atual do AD RMS|Topologia de chave de locatário escolhida do Azure RMS|Instruções de migração|
|-------------------------------|----------------------------------------------------------|--------------------------|
|Proteção por senha no banco de dados do AD RMS|Gerenciado pela Microsoft|Consulte o procedimento **Migração de chave protegida por software para chave protegida por software** depois desta tabela.<br /><br />Esse é o caminho de migração mais simples e requer apenas que você transfira os dados de configuração para o Azure RMS.|
|Proteção de HSM usando um módulo de segurança de hardware (HSM) Thales nShield|Gerenciada pelo cliente (BYOK)|Consulte o procedimento **Migração de chave protegida por HSM para chave protegida por HSM** depois desta tabela.<br /><br />Isso exige que o conjunto de ferramentas BYOK e dois conjuntos de etapas transfiram a chave do seu HSM local para o Azure RMS HSM e depois transfiram os dados de configuração para o Azure RMS.|
|Proteção por senha no banco de dados do AD RMS|Gerenciada pelo cliente (BYOK)|Consulte o procedimento **Migração de chave protegida por software para chave protegida por HSM** depois desta tabela.<br /><br />Isso exige que o conjunto de ferramentas BYOK e três conjuntos de etapas extraiam primeiro sua chave de software e importem-na para um HSM local, depois transfiram a chave de seu HSM local para os HSMs do Azure RMS e, finalmente, transfiram os dados de configuração para o Azure RMS.|
|Proteção de HSM usando um módulo de segurança de hardware (HSM) de um fornecedor que não seja a Thales|Gerenciada pelo cliente (BYOK)|Contate o fornecedor do seu HSM para saber como transferir a sua chave desse HSM para um Módulo de Segurança de Hardware (HSM) Thales nShield. Depois siga as instruções para o procedimento de **Migração de chave protegida por HSM para chave protegida por HSM** depois desta tabela.|
|Senha protegida usando um provedor criptográfico externo|Gerenciada pelo cliente (BYOK)|Contate o fornecedor para o provedor criptográfico para saber como transferir sua chave para um Módulo de Segurança de Hardware (HSM) Thales nShield. Depois siga as instruções para o procedimento de **Migração de chave protegida por HSM para chave protegida por HSM** depois desta tabela.|
Antes de começar estes procedimentos, verifique se você pode acessar os arquivos .xml que você criou antes quando exportou os domínios de publicação confiáveis. Por exemplo, eles podem ter sido salvos em um pen drive USB que você tirou do servidor AD RMS na estação de trabalho conectada à Internet.

> [!NOTE]
> Embora você armazene esses arquivos, use as práticas recomendadas de segurança para protegê-los porque esses dados incluem sua chave privada.

##### Migração de chave protegida por software para chave protegida por software:
Use este procedimento para importar a configuração do AD RMS para o Azure RMS, para resultar na sua chave de locatário do Azure RMS gerenciada pela Microsoft.

###### Para importar os dados de configuração para o Azure RMS

1.  Em uma estação de trabalho conectada à Internet, baixe e instale o módulo do Windows PowerShell para o Azure RMS (versão mínima 2.1.0.0), que inclui o cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx).

    > [!TIP]
    > Se você tiver baixado e instalado o módulo anteriormente, verifique o número da versão executando: `(Get-Module aadrm -ListAvailable).Version`

    Para obter instruções de instalação, consulte [Instalando o Windows PowerShell para Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Inicie o Windows PowerShell com a opção **Executar como administrador** e use o cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) para conectar-se ao serviço do Azure RMS:

    ```
    Connect-AadrmService
    ```
    Quando solicitado, insira suas credenciais de administrador de locatário [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (normalmente, você usará uma conta que seja um administrador global para Active Directory do Azure ou Office 365).

3.  Use o cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) para carregar o primeiro arquivo de domínio de publicação confiável exportado (.xml). Se você tiver mais de um arquivo. xml porque você tinha vários domínios de publicação confiáveis, escolha o arquivo que contenha o domínio de publicação confiável exportado que você deseja usar no Azure RMS para proteger o conteúdo após a migração. Execute o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Por exemplo: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Quando solicitado, digite a senha que você especificou antes e confirme que deseja executar esta ação.

4.  Quando o comando for concluído, repita a etapa 3 para cada arquivo .xml restante que você criou exportando seus domínios de publicação confiáveis. Mas, para estes arquivos, defina **-Active** como **false** quando executar o comando de importação. Por exemplo: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Use o cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) para se desconectar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Agora você está pronto para ir para a [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Migração de chave protegida por HSM para chave protegida por HSM
Esse é um procedimento de duas partes para importar a sua chave HSM e configuração do AD RMS para o Azure RMS, para resultar na sua chave de locatário do Azure RMS gerenciada por você (BYOK).

Primeiro, empacote a sua chave HSM para que assim esteja pronta para ser transferida para o Azure RMS e, em seguida, importe os dados de configuração.

###### Parte 1: Empacotar sua chave HSM para que esteja pronta para transferir para o Azure RMS

1.  Siga as etapas na seção [Implementando trazer a sua própria chave (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) de [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), usando o procedimento **Gerar e transferir a chave de locatário – pela Internet** com as seguintes exceções:

    -   Não siga as instruções para **gerar sua chave de locatário**, porque você já tem o equivalente da sua implantação do AD RMS. Identifique a chave usada pelo servidor do AD RMS na instalação da Thales e use essa chave durante a migração. Os arquivos de chave criptografada Thales geralmente são nomeados **key_(keyAppName)_(keyIdentifier)** localmente no servidor.

    -   Não siga as etapas para **Transferir sua chave de locatário para o Azure RMS**, que usa o comando Add-AadrmKey.  Em vez disso, você transferirá sua chave HSM preparada quando você carregar seu domínio exportado de publicação confiável, usando o comando de importação AadrmTpd.

2.  Na estação de trabalho conectada à Internet, na sessão do Windows PowerShell, reconectar-se ao serviço do Azure RMS.

Agora que você preparou sua chave HSM para o Azure RMS, você está pronto para importar o arquivo de chave de HSM e os dados de configuração do AD RMS.

###### Parte 2: Importe a chave HSM e os dados de configuração para o Azure RMS

1.  Ainda na estação de trabalho conectada à Internet e na sessão do Windows PowerShell, carregue o primeiro arquivo exportado (.xml) do domínio de publicação confiável. Se você tiver mais de um arquivo. xml porque você tinha vários domínios de publicação confiáveis, escolha o arquivo que contenha o domínio de publicação confiável exportado que corresponda à chave HSM que você deseja usar no Azure RMS para proteger o conteúdo após a migração. Execute o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Por exemplo: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Quando solicitado, digite a senha que você especificou antes e confirme que deseja executar esta ação.

2.  Quando o comando for concluído, repita a etapa 1 para cada arquivo .xml que você criou exportando domínios de publicação confiáveis. Mas, para estes arquivos, defina **-Active** como **false** quando executar o comando de importação.  Por exemplo: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Use o cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) para se desconectar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Agora você está pronto para ir para a [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Migração de chave protegida por software para chave protegida por HSM:
Esse é um procedimento de três partes para importar a configuração do AD RMS para o Azure RMS, para resultar na sua chave de locatário do Azure RMS gerenciada por você (BYOK).

Extraia primeiro a sua chave do certificado de licenciante para servidor (SLC) dos dados de configuração e transfira-a para um HSM da Thales local e, em seguida, empacote e transfira a chave HSM para o Azure RMS e importe os dados de configuração.

###### Parte 1: Extrair o SLC dos dados de configuração e importar a chave para o HSM local

1.  Use as seguintes etapas na seção [Implementando trazer a sua própria chave (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)do tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Gerar e transferir a chave de locatário - pela Internet**: **Prepare a sua estação de trabalho conectada à Internet**

    -   **Gerar e transferir a chave de locatário - pela Internet**: **Prepare a sua estação de trabalho desconectada**

    Não siga as instruções para gerar sua chave de locatário, porque você já tem o equivalente no arquivo exportado (.xml) de dados de configuração. Em vez disso, execute um comando para extrair essa chave do arquivo e importá-la para o seu HSM local.

2.  Na estação de trabalho desconectada, execute o seguinte comando:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Por exemplo, para a América do Norte: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Informação adicional:

    -   O parâmetro ImportRmsCentrallyManagedKey indica que a operação é para importar a chave SLC.

    -   Se não especificar a senha no comando, você receberá uma solicitação para especificá-la

    -   O parâmetro KeyIdentifier é um nome de chave fácil que cria o nome do arquivo de chave. Use apenas caracteres ASCII minúsculos.

    -   O parâmetro ExchangeKeyPackage especifica um pacote (KEK) de chave de troca de chaves específica de região que possui um nome que começa com BYOK-KEK-pkg-.

    -   O parâmetro NewSecurityWorldPackage especifica um pacote mundial de segurança específico de região que possui um nome que começa com BYOK-SecurityWorld-pkg-.

    Esse comando resulta no seguinte:

    -   Um arquivo de chave do HSM: %NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;

    -   Arquivo de dados de configuração do RMS com o SLC removido: %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml

3.  Se tiver mais de um arquivo de dados de configuração do RMS, repita a etapa 2 para o restante desses arquivos.

Agora que o SLC foi extraído para ser uma chave baseada em HSM, você já pode empacotá-lo e transferi-lo para o Azure RMS.

###### Parte 2: Empacotar e transferir a sua chave HSM para o Azure RMS

1.  Use as seguintes etapas da seção [Implementando trazer a sua própria chave (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)da [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Gerar e transferir a chave de locatário - pela Internet**: **Prepare sua chave de locatário para transferência**

    -   **Gerar e transferir a chave de locatário - pela Internet**: **Transfira sua chave de locatário para o Azure RMS**

Agora que já transferiu a chave HSM para o Azure RMS, você já pode importar os dados de configuração do AD RMS que contêm somente um ponteiro para a chave de locatário que acabou de ser transferida.

###### Parte 3: Importar os dados de configuração para o Azure RMS

1.  Ainda na estação de trabalho conectada à Internet e na sessão do Windows PowerShell, copie os arquivos de configuração do RMS com o SLC removido (na estação de trabalho desconectada, %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml)

2.  Fazer upload do primeiro arquivo. Se você tiver mais de um arquivo. xml porque você tinha vários domínios de publicação confiáveis, escolha o arquivo que contenha o domínio de publicação confiável exportado que corresponda à chave HSM que você deseja usar no Azure RMS para proteger o conteúdo após a migração. Execute o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Por exemplo: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Quando solicitado, digite a senha que você especificou antes e confirme que deseja executar esta ação.

3.  Quando o comando for concluído, repita a etapa 2 para cada arquivo .xml que você criou exportando seus domínios de publicação confiáveis. Mas, para estes arquivos, defina **-Active** como **false** quando executar o comando de importação. Por exemplo: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Use o cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) para se desconectar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Agora você está pronto para ir para a [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Etapa 3. Ativar o seu locatário do RMS
As informações desta etapa são abordadas totalmente no tópico [Ativando o Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

> [!TIP]
> Se tiver uma assinatura do Office 365, será possível ativar o Azure RMS no Centro de administração do Office 365 ou no Portal clássico do Azure. Recomendamos usar o Portal clássico do Azure, porque você usará esse portal de gerenciamento para concluir a próxima etapa.

**Se o seu locatário do Azure RMS já está ativado?** Se o serviço do Azure RMS já está ativado para a sua organização, os usuários talvez já usaram o Azure RMS para proteger o conteúdo com uma chave de locatário gerada automaticamente (e os modelos padrão) em vez de chaves existentes (e modelos) do AD RMS. Isso é improvável de acontecer em computadores que estão bem gerenciados em sua intranet, pois eles serão configurados automaticamente para sua infraestrutura do AD RMS. Mas isso pode acontecer em computadores do grupo de trabalho ou computadores que raramente se conectam à sua intranet. Infelizmente, também é difícil identificar esses computadores, por isso, recomendamos que você não ative o serviço antes de importar os dados de configuração do AD RMS.

Se seu locatário do Azure RMS já estiver ativado e você pode identificar tais computadores, certifique-se de que você executa o script CleanUpRMS_RUN_Elevated.cmd nesses computadores, conforme descrito na etapa 5. A execução deste script força a reinicializar o ambiente do usuário, para que eles baixem a chave de locatário atualizada e os modelos importados.

### <a name="BKMK_Step4Migration"></a>Etapa 4. Configurar modelos importados
Como os modelos importados têm um estado padrão de **Arquivado**, você deve alterar esse estado para ser**Publicado**se desejar que os usuários possam utilizá-los com o Azure RMS.

Além disso, se seus modelos no AD RMS usaram o grupo **QUALQUER PESSOA**, este grupo será removido automaticamente quando você importar os modelos para o Azure RMS; é necessário adicionar manualmente o grupo ou os usuários equivalentes e os mesmos direitos aos modelos importados. O grupo equivalente para o Azure RMS é denominado **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**. Por exemplo, este grupo pode parecer com o item seguinte, para Contoso: **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

Se você não tiver certeza se seus modelos do AD RMS incluem o grupo ANYONE, expanda a seção [PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE) nesta etapa para copiar e usar o exemplo de script do PowerShell para identificar esses modelos. Para obter mais informações sobre como usar o Windows PowerShell com o AD RMS, consulte a seção [Como usar o Windows PowerShell para administrar o AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Você poderá ver o grupo de sua organização criado automaticamente se copiar um dos modelos de política de direitos padrão no Portal clássico do Azure e, em seguida, identificar o **NOME DE USUÁRIO** na página **DIREITOS**. No entanto, você não poderá usar o Portal clássico do Azure para adicionar esse grupo a um modelo criado manualmente ou importado. Em vez disso, deverá usar uma das opções do Azure RMS PowerShell:

-   Use o cmdlet do PowerShell [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) para definir o grupo "AllStaff" e os direitos como um objeto de definição de direitos e execute este comando novamente para cada um dos outros grupos ou usuários com direitos já concedidos no modelo original além do grupo ANYONE. Em seguida, adicione esses objetos de definição de direitos aos modelos usando o cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx).

-   Use o cmdlet [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) para exportar o modelo para um arquivo .XML que você pode editar para adicionar o grupo "AllStaff" e os direitos aos grupos e direitos existentes e, em seguida, use o cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) para importar esta mudança de volta para o Azure RMS.

> [!NOTE]
> Este grupo equivalente "AllStaff" não é exatamente o mesmo que o grupo que QUALQUER PESSOA no AD RMS:  O grupo "AllStaff" inclui todos os usuários em seu locatário do Azure, considerando que o grupo TODAS AS PESSOAS inclui todos os usuários autenticados, que poderiam estar fora da sua organização.
> 
> Devido a esta diferença entre os dois grupos, talvez seja necessário também adicionar usuários externos, além do grupo "AllStaff". Atualmente, não há suporte para endereços de email externos para grupos.

Os modelos que você importar do AD RMS terão a aparência e o comportamento iguais aos modelos personalizados que você pode criar no Portal clássico do Azure. Para alterar os modelos importados para serem publicados de forma que os usuários possam vê-los e selecioná-los em aplicativos ou fazer outras mudanças nos modelos, veja [Configurando modelos personalizados do Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> Para dar aos usuários uma experiência mais consistente durante o processo de migração, não faça alterações aos modelos importados além destas duas alterações; e não publique os dois modelos padrão fornecidos com o Azure RMS nem crie novos modelos no momento. Em vez disso, aguarde a conclusão do processo de migração e encerre os servidores AD RMS.

#### <a name="BKMK_ScriptForANYONE"></a>Exemplo de script do Windows PowerShell para identificar modelos do AD RMS que incluem o grupo ANYONE
Esta seção contém o script de exemplo para ajudar a identificar modelos do AD RMS que têm o grupo ANYONE definido, conforme descrito na seção anterior.

*&#42;&#42;Aviso de isenção de responsabilidade&#42;&#42;: Não há suporte para esse script de exemplo em qualquer serviço ou programa de suporte padrão da Microsoft. Esse script de exemplo é fornecido como está sem garantias de qualquer tipo.*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>Etapa 5. Reconfigurar clientes para usar o Azure RMS
Para clientes Windows:

1.  [Baixe os scripts de migração](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Esses scripts redefinem a configuração em computadores com Windows para que os mesmos usem o serviço do Azure RMS em vez do AD RMS.

2.  Siga as instruções no script de redirecionamento (Redirect_OnPrem.cmd) modificando-o para apontar para o novo locatário do Azure RMS.

3.  Nos computadores Windows, execute esses scripts com privilégios elevados no contexto do usuário.

Para clientes de dispositivos móveis e computadores Mac:

-   Remova os registros SRV do DNS criados quando você implantou a [extensão de dispositivos móveis AD RMS](http://technet.microsoft.com/library/dn673574.aspx).

#### Alterações feitas pelos scripts de migração
Esta seção documenta as alterações feitas pelos scripts de migração. Use essas informações apenas para referência, para solucionar problemas ou, se preferir, para fazer essas alterações por conta própria.

CleanUpRMS_RUN_Elevated.cmd:

-   Exclua o conteúdo das pastas %userprofile%\AppData\Local\Microsoft\DRM e %userprofile%\AppData\Local\Microsoft\MSIPC, incluindo todas as subpastas e todos os arquivos com nomes de arquivo longos.

-   Exclua o conteúdo das seguintes chaves de registro:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Exclua os seguintes valores de registro:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Crie os seguintes valores de registro para cada URL fornecida como um parâmetro em cada um destes locais:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Cada entrada tem um valor REG_SZ de **https://OldRMSserverURL/_wmcs/licensing** with the data in the following format: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt; YourTenantURL &gt;* tem o seguinte formato: **{GUID} .rms. [Região].aadrm.com**.
    > 
    > Por exemplo:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Você pode encontrar esse valor por meio da identificação do valor **RightsManagementServiceId** quando você executar o cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) para o Azure RMS.

### <a name="BKMK_Step6Migration"></a>Etapa 6. Configurar a integração do IRM com o Exchange Online
Se tiver importado anteriormente o TDP do AD RMS para o Exchange Online, você deve remover essa TDP para evitar modelos e políticas conflitantes depois de migrar para o Azure RMS. Para o fazer, use o cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) do Exchange Online.

Se você escolher uma topologia de chave de locatário do Azure RMS que seja **gerida pela Microsoft**:

-   Consulte a seção [Exchange Online: Configuração do IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) no tópico [Configurando aplicativos do Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md). Esta seção inclui comandos típicos para executar que se conectam ao serviço Exchange Online, importam a chave de locatário do Azure RMS e habilita a funcionalidade do IRM para o Exchange Online. Depois de concluir tais etapas, você terá a funcionalidade completa do RMS com o Exchange Online.

Se você escolher uma topologia de chave de locatário do Azure RMS que seja **gerida pelo cliente (BYOK)**:

-   Terá uma funcionalidade do RMS com o Exchange Online reduzida, conforme descrito na seção [Preços e restrições do BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) no tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

### <a name="BKMK_Step7Migration"></a>Etapa 7. Implantar o conector RMS
Se usou a funcionalidade de Gerenciamento de Direitos de Informação (IRM) do Exchange Server ou do SharePoint Server com o AD RMS, primeiro desative o IRM nesses servidores e remova a configuração do AD RMS. Em seguida, implante o conector do Rights Management (RMS), que atua como uma interface de comunicação (um retransmissor) entre os servidores locais e o Azure RMS.

Por fim, nesta etapa, se importou vários TPDs para o Azure RMS que foram usados para proteger as mensagens de email, edite manualmente o registro nos computadores do Exchange Server para redirecionar todas as URLs de TPDs para o conector RMS.

> [!NOTE]
> Antes de começar, verifique as versões com suporte dos servidores locais que tem suporte para o conector RMS “servidores locais que têm suporte para o Azure RMS” na seção [Aplicativos que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications)do tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

##### Desativar o IRM nos Exchange Servers e remover a configuração do AD RMS

1.  Em cada Exchange Server, localize a seguinte pasta e exclua todas as entradas da mesma: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Em um dos Exchange Servers, use o cmdlet [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) do Exchange para primeiro desativar os recursos do IRM para as mensagens enviadas para destinatários internos:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Em seguida, use o mesmo cmdlet para desabilitar recursos do IRM para mensagens enviadas a destinatários externos:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Use o mesmo cmdlet para desabilitar o IRM no Microsoft Office Outlook Web App e dn Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Por fim, use o mesmo cmdlet para limpar todos os certificados armazenados em cache:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Em cada servidor do Exchange, redefina o IIS, por exemplo, executando um prompt de comando como um administrador e digitando **iisreset**.

##### Desativar o IRM nos SharePoint Servers e remover a configuração do AD RMS

1.  Certifique-se de que não haja nenhum documento desmarcado das bibliotecas protegidas pelo RMS. Se houver, eles ficarão inacessíveis no final deste procedimento.

2.  No site da Administração Central do SharePoint, na seção**Início Rápido**, clique em**Segurança**.

3.  Na página de **Segurança** na seção **Diretiva de informações**, clique em**Configurar o gerenciamento de direitos de informação**.

4.  Na página de **Gerenciamento de Direitos de Informação**, na seção **Gerenciamento de Direitos de Informação**, selecione**Não usar o IRM neste servidor** e clique em**OK**.

5.  Em cada um dos computadores do SharePoint Server, exclua o conteúdo da pasta \ProgramData\Microsoft\MSIPC\Server\*&lt;SID da conta que está usando o SharePoint Server&gt;*.

##### Instalar e configurar o conector RMS

-   Use as instruções no tópico [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

##### Somente para o Exchange e vários TPDs: Editar o registro

-   Em cada Exchange Server, adicione manualmente as chaves de registro abaixo para cada TPD adicional que você importou para redirecionar as URLs do TPD para o conector RMS. Essas entradas de registro são específicas para a migração e não são adicionadas pela ferramenta de configuração do servidor para o conector Microsoft RMS.

    Ao fazer essas edições de registro, use estas instruções:

    -   Substitua o *ConnectorFQDN*com o nome que você definiu no DNS para o conector. Por exemplo, **rmsconnector.contoso.com**.

    -   Use o prefixo HTTPS ou HTTPS para a URL do conector se você tiver configurado o conector para usar HTTPS ou HTTPS para se comunicar com os servidores locais.

    **Para o Exchange 2013:**

    |Registrar caminho|Tipo|Valor|Dados|
    |---------------------|--------|---------|---------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;URL da Intranet de licenciamento do AD RMS&gt;/_wmcs/licensing|Um dos seguintes, dependendo se você estiver usando HTTP ou HTTPS do servidor Exchange para o conector RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;URL da Extranet de licenciamento do AD RMS&gt;/_wmcs/licensing|Um dos seguintes, dependendo se você estiver usando HTTP ou HTTPS do servidor Exchange para o conector RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **Para o Exchange Server 2010:**

    |Registrar caminho|Tipo|Valor|Dados|
    |---------------------|--------|---------|---------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;URL da Intranet de licenciamento do AD RMS&gt;/_wmcs/licensing|Um dos seguintes, dependendo se você estiver usando HTTP ou HTTPS do servidor Exchange para o conector RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;URL da Extranet de licenciamento do AD RMS&gt;/_wmcs/licensing|Um dos seguintes, dependendo se você estiver usando HTTP ou HTTPS do servidor Exchange para o conector RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|

Após concluir esses procedimentos, certifique-se de ler a seção **Próximas etapas** no tópico [Implantando o conector do Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_Step8Migration"></a>Etapa 8. Descomissionamento do AD RMS
Opcional: Remova o ponto de conexão de serviço (SCP) do Active Directory para impedir que os computadores descubram sua infraestrutura de gerenciamento de direitos local. Isso é opcional por causa do redirecionamento configurado no registro (por exemplo, executando o script de migração). Para remover o Ponto de Conexão de Serviço, use AD SCP Register de [Rights Management Services Administration Toolkit](http://www.microsoft.com/download/details.aspx?id=1479).

Monitore os seus servidores AD RMS para atividade, por exemplo, verificando as [solicitações no relatório de Integridade do sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou [a auditoria de acesso do usuário ao conteúdo protegido](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Depois de confirmar que os clientes RMS não estão se comunicando com esses servidores e os clientes estão usando o Azure RMS com sucesso, remova a função de servidor do AD RMS desse servidor. Se estiver usando servidores dedicados, talvez você prefira a etapa preventiva de desligar primeiro os servidores por um tempo para garantir que não haja nenhum problema que talvez exija a reinicialização desses servidores para garantir a continuidade do serviço enquanto você investiga por que os clientes não estão usando o Azure RMS.

Após o encerramento dos servidores de AD RMS, você pode querer aproveitar a oportunidade para examinar os modelos no Portal clássico do Azure e consolidá-los para que os usuários tenham menos modelos para escolha ou reconfigurá-los ou até mesmo adicionar novos modelos. Esse também é um bom momento para publicar os modelos padrão. Para obter mais informações, consulte [Configurando modelos personalizados do Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>Etapa 9. Criar novamente a sua chave de locatário do Azure RMS
Esta etapa é necessária quando a migração é concluída, se sua implantação do AD RMS estava usando o Modo de Criptografia 1 do RMS, porque a recriação cria uma nova chave de locatário que usa o Modo de Criptografia 2 do RMS. Usar o Azure RMS com modo de criptografia 1 é suportado apenas durante o processo de migração.

Esta etapa é opcional, mas recomendada quando a migração é concluída, mesmo se estivesse operando no Modo de Criptografia 2 do RMS, pois ajuda a proteger a sua chave de locatário do Azure RMS contra possíveis violações de segurança na sua chave de AD RMS. Quando você cria novamente sua chave de locatário do Azure RMS (também conhecido como “distribuir sua chave”), uma nova chave é criada e a chave original é arquivada. No entanto, como a mudança de uma chave para outra não acontece imediatamente, pois leva semanas, não espere até suspeitar de uma violação na chave original. Crie novamente sua chave de locatário RMS assim que a migração for concluída.

Para criar novamente sua chave de locatário do Azure RMS:

-   Se a chave de locatário do RMS for gerenciada pela Microsoft: Ligue para o Suporte ao Cliente da Microsoft (CSS) e prove que você é o administrador do locatário do RMS.

-   Se a chave de locatário do RMS for gerenciada por você (BYOK): Repita o procedimento BYOK para gerar e criar uma nova chave pela Internet ou pessoalmente.

Para obter mais informações sobre como gerenciar sua chave de locatário do RMS, consulte [Operações para Sua chave de locatário do Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Consulte também
[Configurando o Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

