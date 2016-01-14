---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Opera&#231;&#245;es para Sua chave de locat&#225;rio do Azure Rights Management
Dependendo da topologia da sua chave de locatário (gerenciada pela Microsoft ou gerenciada pelo cliente), você tem diferentes níveis de controle e responsabilidade para sua chave de locatário do Microsoft Azure Rights Management (Azure RMS) após ser implantado.

Quando você gerencia sua própria chave de locatário, esta é geralmente chamada de trazer sua própria chave (BYOK). Para obter mais informações sobre este cenário e de como escolher entre as duas topologias de chave de locatário, consulte [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

A tabela a seguir identifica as operações que você pode realizar, dependendo da topologia escolhida para sua chave de locatário do Azure RMS.

|Operação do ciclo de vida|Gerenciada pela Microsoft (padrão)|Gerenciada pelo cliente (BYOK)|
|-----------------------------|--------------------------------------|----------------------------------|
|Revogue sua chave de locatário|Não (automático)|Não (automático)|
|Crie novamente sua chave de locatário|Sim|Sim|
|Faça backup e recupere sua chave de locatário|Não|Sim|
|Exportar sua chave de locatário|Sim|Não|
|Responder a uma violação|Sim|Sim|
Depois de ter identificado a topologia que você implementou, use uma das seções a seguir para obter mais informações sobre estas operações para sua chave de locatário do Azure RMS.

## <a name="BKMK_MSManagedOperations"></a>Gerenciado pela Microsoft: Operações do ciclo de vida da chave de locatário
Se a Microsoft gerencia sua chave de locatário para o Azure Rights Management (o padrão), use as seções a seguir para obter mais informações sobre as operações do ciclo de vida que são relevantes para esta topologia:

-   [Revogue sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Crie novamente sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Faça backup e recupere sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [Exportar sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Responder a uma violação](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>Revogue sua chave de locatário
Ao cancelar a assinatura do Azure RMS, o Azure RMS para de usar sua chave de locatário e não precisa realizar nenhuma ação.

### <a name="BKMK_MSRekey"></a>Crie novamente sua chave de locatário
A Criação repetida de chaves também é conhecida como geração repetida de sua chave. Não crie novamente sua chave de locatário a menos que seja realmente necessário. Clientes antigos, tais como Office 2010, não foram projetados para manipular normalmente as alterações de chave. Neste cenário, você deve limpar o estado do RMS nos computadores usando uma Política de grupo ou um mecanismo equivalente. Entretanto, há alguns eventos legítimos que podem lhe forçar a criar novamente sua chave de locatário. Por exemplo:

-   Sua empresa se dividiu em duas ou mais empresas. Ao criar novamente sua chave de locatário, a nova empresa não terá acesso ao novo conteúdo que seus empregados publiquem. Eles podem acessar o conteúdo antigo se tiverem uma cópia da chave de locatário antiga.

-   Você acredita que a cópia mestre da sua chave de locatário (a cópia em sua posse) foi comprometida.

Você pode criar novamente sua chave de locatário chamando ao CSS (Serviços de Atendimento ao Cliente) da Microsoft e provando que você é o administrador de locatário.

Ao criar novamente sua chave de locatário, o novo conteúdo é protegido usando a nova chave de locatário. Isto acontece em uma maneira em fases, para que em um período de tempo, algum conteúdo novo continuará sendo protegido com a chave de locatário antiga. O conteúdo previamente protegido permanece protegido com sua chave de locatário antiga. Para oferecer suportes a este cenário, o Azure RMS retém sua chave de locatário antiga de modo que possa emitir licenças para conteúdo antigo.

### <a name="BKMK_MSBackup"></a>Faça backup e recupere sua chave de locatário
A Microsoft é responsável por fazer o backup da sua chave de locatário e nenhuma ação sua é requerida.

### <a name="BKMK_MSExport"></a>Exportar sua chave de locatário
Você pode exportar sua configuração do Azure RMS e a chave do locatário seguindo as instruções nestas três etapas:

##### Etapa 1: Iniciar exportação

-   Para fazer isso, contate o Serviço de Atendimento ao Cliente da Microsoft (CSS). Você deve provar que é um administrador para seu locatário do Azure RMS.

##### Etapa 2: Espere a verificação

-   A Microsoft verifica se sua solicitação de liberação da chave de locatário do RMS é legítima. Esse processo pode levar até três semanas.

##### Etapa 3: Receber instruções de chave do CSS

-   Os Serviços de Atendimento ao Cliente da Microsoft (CSS) lhe enviarão sua configuração do Azure RMS e a chave de locatário criptografada em um arquivo protegido por senha que tem a extensão de nome de arquivo .tpd. Para fazer isto, o CSS primeiro lhe envia (como a pessoa que inicia a exportação) uma ferramenta por e-mail. Você deve executar a ferramenta desde um prompt de comando da seguinte forma:

    ```
    AadrmTpd.exe -createkey
    ```
    Isso gera um par de chaves do RSA e salva as metades pública e privada como arquivos na pasta atual. Por exemplo: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** e **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Responda a este email a partir do CSS, anexando o arquivo com um nome que comece com **PublicKey**. O CSS enviará um arquivo TPD como um arquivo .xml que é criptografado com sua chave RSA. Copie esse arquivo para a mesma pasta em que você executou a ferramenta AadrmTpd originalmente e execute-a novamente, usando o arquivo que começa com **PrivateKey** e o arquivo de CSS. Por exemplo:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    A saída deste comando deveria ser dois arquivos: Um contem a senha em texto sem formatação para o TDP protegido por senha e o outro é o TPD protegido por senha próprio. Para propósitos de referências cruzadas, ambos devem ter o mesmo GUID que os arquivos de chave públicos e privados no momento em que você executou o comando AadrmTpd.exe -createkey:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Faça backup destes arquivos e armazene-os com segurança para garantir que você possa continuar descriptografando conteúdo protegido com esta chave de locatário. Além disso, se você estiver migrando para o AD RMS, você pode importar este arquivo TPD (o arquivo que começa com **ExportedTDP**) para seu servidor do AD RMS.

##### Etapa 4: Contínua: proteger sua chave de locatário

-   Após receber sua chave de locatário, guarde-a em local seguro, pois se alguém tiver acesso a ela será possível descriptografar todos os documentos protegidos usando essa chave.

    Caso queira exportar sua chave de locatário porque não deseja mais usar o Azure RMS, a prática recomendada é desativar seu locatário do RMS. Não demore para fazer isso após receber sua chave de locatário, pois isso o ajudará a minimizar as consequências se sua chave for acessada por alguém que não deveria ter acesso a ela. Para obter instruções, consulte [Encerramento e desativação do Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Responder a uma violação
Nenhum sistema de segurança, sem importar o forte que seja, está completo sem um processo de resposta de violação. Sua chave de locatário pode estar comprometida ou roubada. Ainda quando estiver bem protegido, as vulnerabilidades podem ser encontradas na tecnologia HSM da geração atual ou em comprimentos e algoritmos da chave atual.

A Microsoft tem uma equipe dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que houver um relatório confiável de um incidente, esta equipe se ocupa de investigar o escopo, a causa raiz e as atenuações. Se este incidente afeta seus ativos, então a Microsoft notificará seus administradores de locatário do Azure RMS por e-mail usando o endereço que você forneceu quando assinou.

Se você detectar uma violação, a melhor ação que você ou a Microsoft pode efetuar depende do escopo da violação; a Microsoft trabalhará com você ao longo deste processo. A seguinte tabela mostra algumas situações típicas e a resposta provável, embora a resposta exata dependerá de todas as informações que sejam reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|--------------------------|---------------------|
|Sua chave de locatário vazou.|Crie novamente sua chave de locatário. Consulte a seção [Crie novamente sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) neste tópico.|
|Um indivíduo não autorizado ou malware obteve direitos para usar sua chave de locatário mas a chave em si não vazou.|Criar novamente sua chave de locatário não ajuda aqui e necessita um análises da causa raiz. Se um processo ou bug do software foi responsável para que o indivíduo não autorizado obtenha acesso, aquela situação deve ser resolvida.|
|Vulnerabilidade descoberta no algoritmo RSA, ou comprimento da chave, ou ataques de força bruta se tornam possíveis em termos computacionais.|A Microsoft deve atualizar o Azure RMS para oferecer suporte de novos algoritmos e comprimentos de chave maiores que sejam resilientes, e instruir a todos os usuários a renovar suas chaves de locatário.|

## <a name="BKMK_BYOKManagedOperations"></a>Gerenciada pelo cliente: Operações do ciclo de vida da chave de locatário
Se você gerencia sua chave de locatário para o Azure Rights Management (o cenário traz sua própria chave, ou BYOK), use as seções a seguir para obter mais informações sobre as operações do ciclo de vida que são relevantes para esta topologia:

-   [Revogue sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Crie novamente sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Faça backup e recupere sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [Exportar sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Responder a uma violação](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>Revogue sua chave de locatário
Ao cancelar a assinatura do Azure RMS, o Azure RMS para de usar sua chave de locatário e não precisa realizar nenhuma ação.

### <a name="BKMK_BYOKRekey"></a>Crie novamente sua chave de locatário
A Criação repetida de chaves também é conhecida como geração repetida de sua chave. Não crie novamente sua chave de locatário a menos que seja realmente necessário. Clientes antigos, tais como Office 2010, não foram projetados para manipular normalmente as alterações de chave. Neste cenário, você deve limpar o estado do RMS nos computadores usando uma Política de grupo ou um mecanismo equivalente. Entretanto, há alguns eventos legítimos que podem lhe forçar a criar novamente sua chave de locatário. Por exemplo:

-   Sua empresa se dividiu em duas ou mais empresas. Ao criar novamente sua chave de locatário, a nova empresa não terá acesso ao novo conteúdo que seus empregados publiquem. Eles podem acessar o conteúdo antigo se tiverem uma cópia da chave de locatário antiga.

-   Você acredita que a cópia mestre da sua chave de locatário (a cópia em sua posse) foi comprometida.

Ao criar novamente sua chave de locatário, o novo conteúdo é protegido usando a nova chave de locatário. Isto acontece em uma maneira em fases, para que em um período de tempo, algum conteúdo novo continuará sendo protegido com a chave de locatário antiga. O conteúdo previamente protegido permanece protegido com sua chave de locatário antiga. Para oferecer suportes a este cenário, o Azure RMS retém sua chave de locatário antiga de modo que possa emitir licenças para conteúdo antigo.

Você pode gerar e criar novamente sua chave de locatário pela Internet ou pessoalmente, usando os procedimentos na seção[Implementando trazer a sua própria chave (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) do tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

### <a name="BKMK_BYOKBackup"></a>Faça backup e recupere sua chave de locatário
Você é responsável por fazer o backup da sua chave de locatário. Se você gerou sua chave de locatário em um Thales HSM, para fazer o backup da chave, simplesmente faça o backup do arquivo de Chave de token, o arquivo World e os Cartões de administrador.

Se você transferiu sua chave seguindo os procedimentos na seção [Implementando trazer a sua própria chave (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) do tópico [Planejando e implementando sua chave de locatário do Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), o Azure RMS persistirá o Arquivo de chave de token, para proteger contra falhas de qualquer nó do Azure RMS. No entanto, não considere isto como um backup completo. Por exemplo, se você alguma vez precisar uma cópia em texto não formatado da sua chave para usar fora de um Thales HSM, o Azure RMS não será capaz de recuperá-la para você porque somente tem uma cópia não recuperável.

### <a name="BKMK_BYOKExport"></a>Exportar sua chave de locatário
Se você usa o BYOK, você não pode exportar sua chave de locatário do Azure RMS. A cópia no Azure RMS não é recuperável. Se desejar excluir essa chave para que ela não possa mais ser usada, entre em contato com o suporte de serviço de cliente da Microsoft (CSS).

### <a name="BKMK_BYOKBreach"></a>Responder a uma violação
Nenhum sistema de segurança, sem importar o forte que seja, está completo sem um processo de resposta de violação. Sua chave de locatário pode estar comprometida ou roubada. Ainda quando estiver bem protegido, as vulnerabilidades podem ser encontradas na tecnologia HSM da geração atual ou em comprimentos e algoritmos da chave atual.

A Microsoft tem uma equipe dedicada para responder a incidentes de segurança nos seus produtos e serviços. Assim que houver um relatório confiável de um incidente, esta equipe se ocupa de investigar o escopo, a causa raiz e as atenuações. Se este incidente afeta seus ativos, então a Microsoft notificará seus administradores de locatário do Azure RMS por e-mail usando o endereço que você forneceu quando assinou.

Se você tem uma violação, a melhor ação que você ou a Microsoft podem tomar depende do escopo da violação; a Microsoft trabalhará com você ao longo deste processo. A seguinte tabela mostra algumas situações típicas e a resposta provável, embora a resposta exata dependerá de todas as informações que sejam reveladas durante a investigação.

|Descrição do incidente|Resposta provável|
|--------------------------|---------------------|
|Sua chave de locatário vazou.|Crie novamente sua chave de locatário. Consulte a seção [Crie novamente sua chave de locatário](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) neste tópico.|
|Um indivíduo não autorizado ou malware obteve direitos para usar sua chave de locatário mas a chave em si não vazou.|Criar novamente sua chave de locatário não ajuda aqui e necessita um análises da causa raiz. Se um processo ou bug do software foi responsável para que o indivíduo não autorizado obtenha acesso, aquela situação deve ser resolvida.|
|A vulnerabilidade descoberta na tecnologia HSM da geração atual.|A Microsoft deve atualizar os HSMs. Se há um motivo para acreditar que a vulnerabilidade expus as chaves, então a Microsoft instruirá a todos os clientes para renovar suas chaves de locatário.|
|Vulnerabilidade descoberta no algoritmo RSA, ou comprimento da chave, ou ataques de força bruta se tornam possíveis em termos computacionais.|A Microsoft deve atualizar o Azure RMS para oferecer suporte de novos algoritmos e comprimentos de chave maiores que sejam resilientes, e instruir a todos os usuários a renovar suas chaves de locatário.|

## Consulte também
[Usando o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

