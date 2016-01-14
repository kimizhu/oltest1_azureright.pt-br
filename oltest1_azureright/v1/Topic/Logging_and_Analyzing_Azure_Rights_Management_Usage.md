---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Registrando em log e analisando o uso do Azure Rights Management
Use as informações neste tópico para ajudá-lo a entender como usar registro em log com o Azure Rights Management (Azure RMS). O serviço Azure Rights Management pode registrar cada solicitação feita para sua organização, incluindo solicitações de usuários, ações realizadas por administradores do Rights Management na sua organização e ações realizadas por operadores da Microsoft para dar suporte a sua implantação do Azure Rights Management.

Você pode usar esses logs do Azure Rights Management dar oferecer suporte aos cenários de negócios a seguir:

-   Analisar ideias de negócios.

    O Azure Rights Management grava logs no formato de log estendido W3C na conta de armazenamento do Azure que você fornece. Você pode em seguida direcionar estes logs em um repositório de sua escolha (como um banco de dados, um sistema de processamento analítico online (OLAP), ou um sistema de redução de mapa) Como um exemplo, você pode identificar quem está acessando seus dados protegidos pelo RMS. Você pode determinar quais dados protegidos pelo RMS as pessoas acessam e de quais dispositivos e de onde. Você pode descobrir se as pessoas podem ler com êxito o conteúdo protegido. Você também pode identificar quais pessoas leram um documento importante que foi protegido.

-   Monitorar o abuso.

    As informações de registro em log do Azure Rights Management estão disponíveis para você em tempo quase real, para que você possa monitorar continuamente o uso do Rights Management por sua empresa. 99.9% dos logs estão disponíveis após 15 minutos de uma ação iniciada pelo RMS.

    Por exemplo, você pode querer se alertado se há um aumento repentino de pessoas lendo os dados protegidos pelo RMS fora das horas de trabalho padrão, que pode indicar que um usuário mal-intencionado está coletando informações para vendê-las a concorrentes. Ou, se o mesmo usuário aparentemente acessa dados de dois endereços de IP diferentes em um intervalo de tempo curto, que pode indicar que uma conta de usuário foi comprometida.

-   Executar análise forense.

    Se você tiver um vazamento de informação, é provável que seja solicitado quem acessou recentemente documentos específicos e que informações a pessoa suspeitosa acessou recentemente. Você pode responder a esse tipo de pergunta quando usa o Azure Rights Management e o registro em log porque as pessoas que usam o conteúdo protegido sempre devem obter uma licença do Rights Management para abrir documentos e imagens que sejam projetadas pelo Azure Rights Management, mesmo se esses arquivos são movidos por email ou copiados para unidades USB ou outros dispositivos de armazenamento. Isso significa que você pode usar os logs do Azure Rights Management como uma fonte definitiva de informações para análise forense quando você protege seus dados usando o Azure Rights Management.

> [!NOTE]
> Se você estiver interessado somente no registro em log de tarefas administrativas para o Azure Rights Management e não quiser controlar como os usuários estão usando o Rights Management, poderá usar o cmdlet [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) do Windows PowerShell do Azure Rights Management.
> 
> Você também pode usar o Azure Classic Portal para relatórios de uso de alto nível que incluem **uso do RMS**, **usuários RMS mais ativos**, **uso do dispositivo RMS** e **uso do aplicativo habilitado com RMS**. Para acessar esses relatórios no Azure Classic Portal, clique em **Active Directory**, selecione e abra um diretório e clique em **RELATÓRIOS**,

Use as seguintes seções para obter mais informações sobre registro em log do uso do Azure Rights Management:

-   [Como habilitar o registro em log do uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Como acessar e usar seus logs de uso Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Como gerenciar o armazenamento de log do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Como delegar acesso a seus logs de uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Como interpretar seus logs de uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Referência do Windows PowerShell](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Como habilitar o registro em log do uso do Azure Rights Management
O registro em log do uso do Azure Rights Management é opcional, portanto, se você quer usá-lo, deve seguir etapas específicas. Ao usar o registro em log de uso do Azure Rights Management, não há mudanças em como o Rights Management trabalha e o processo de log em si é gratuito. Entretanto, você deve fornecer uma conta de armazenamento do Azure para os logs e você será cobrado por este armazenamento.

Antes de começar, certifique-se de atender os seguintes pré-requisitos para usar o registro em log do Azure Rights Management:

|Requisito|Mais informações|
|-------------|--------------------|
|Confirme se você tem uma assinatura de TI gerenciada que inclui o Azure Rights Management|Você deve ter uma assinatura do Microsoft Azure Rights Management que seja gerenciada por sua organização. As organizações que usam o RMS para pessoa física não podem usar o registro em log de uso do Azure Rights Management .<br /><br />Se sua organização tem usuários que usam o RMS para pessoa física, o registro em log de uso do Azure Rights Management fornece um motivo comercial muito convincente para converter o RMS para pessoa física em uma assinatura do Microsoft Azure Rights Management .<br /><br />Para obter mais informações sobre as assinaturas que incluem o Azure RMS, consulte a seção [Assinaturas de nuvem que suportam o Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) no tópico [Requisitos para o Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Para obter mais informações sobre o RMS para pessoas físicas, consulte [RMS para pessoas físicas e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).|
|Assinatura do Azure|Você deve ter uma assinatura do Azure e armazenamento suficiente no Azure para seus logs do Rights Management.|
|Windows PowerShell para Azure Rights Management|Se ainda não tiver feito isso, baixe e instale o módulo do Windows PowerShell para o Azure Rights Management. Você usará os cmdlets do Windows PowerShell para configurar e gerenciar seus logs de uso do Azure Rights Management.<br /><br />Para obter mais informações, consulte [Instalando o Windows PowerShell para Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
Use o seguinte procedimento para habilitar o registro em log de uso do Azure Rights Management, que inclui as etapas para criar uma conta de armazenamento do Azure e depois configurar o Azure para usar essa conta de armazenamento para seus logs do Rights Management.

> [!NOTE]
> Este procedimento pressupõe que você tem uma conta do Azure. O registro em log de uso do Azure Rights Management dá suporte a contas de pessoa física, mas a prática recomendada é usar contas de trabalho ou escolares. Além disso, recomendamos que crie uma conta de armazenamento dedicada para seus logs do Rights Management. Você deve compartilhar as chaves de acesso de armazenamento com o Azure Rights Management e possivelmente com outras pessoas, se elas também usam os arquivos de log.
> 
> Para obter mais informações sobre o armazenamento do Azure, consulte a [Documentação do Azure para armazenamento](http://azure.microsoft.com/documentation/services/storage/).

#### Como criar sua conta de armazenamento e habilitar registro em log de uso do Azure Rights Management

1.  Entre no [Portal do Azure](https://portal.azure.com/).

2.  No menu Hub, selecione **Novo** -&gt; **Dados + Armazenamento** -&gt; **Conta de armazenamento**.

    > [!TIP]
    > Se não ver essa opção, verifique se você tem uma assinatura do Azure além de sua assinatura do gerenciamento de direitos.

3.  Mantenha o modelo de implantação padrão de **Classic**, e em seguida, clique em **Criar**.

    Especifique o nome para sua conta de armazenamento e, se necessário, altere as opções selecionadas para **Camada de preços**, **Grupo de Recursos**, **Assinatura** e se deseja **Fixar no painel**. e clique em **CRIAR**. Espere a atividade **Criando conta de armazenamento** ser concluída.

4.  Clique na conta de armazenamento recém-criada e clique em **Configurações**.

5.  Na folha **Configurações**, clique no **Chaves**.

6.  Na folha **Gerenciar chaves**, copie o valor da  **CHAVE DE ACESSO PRIMÁRIO** e feche a folha.

7.  Inicie o Windows PowerShell com a opção **Executar como administrador**. Execute o comando [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) para conectar-se ao serviço do Azure Rights Management:

    ```
    Connect-AadrmService
    ```

8.  Use o comando [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) para especificar onde deseja manter os logs de uso do Azure Rights Management, substituindo *&lt;Access_Key&gt;* pela chave de acesso primária que copiou na etapa 6 e *&lt;StorageAccount&gt;* pelo nome da conta de armazenamento que criou na etapa 3:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Use o comando [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) para habilitar o registro em log de uso do Azure Rights Management:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Você deverá ver a mensagem: **O recurso de log de uso é habilitado para o serviço de Rights management.**

Agora que o registro em log de uso está habilitado, o Azure Rights Management começa registrar todas as ações para sua organização e salva essas informações na sua conta de armazenamento. As informações de log não estão disponíveis antes deste ponto.

Para obter mais informações sobre como criar contas de armazenamento, consulte a seção [Criar uma conta de armazenamento](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) em [Sobre contas de armazenamento do Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) na documentação do Azure.

## <a name="BKMK_AccesAndUseLogs"></a>Como acessar e usar seus logs de uso Azure Rights Management
O Azure Rights Management grava logs na sua conta de armazenamento do Azure como uma série de blobs. Cada blob contém um ou mais registros de log, no formato de log estendido W3C. Os nomes de blob são números, na ordem em que eles são criados. A seção [Como interpretar seus logs de uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) mais adiante neste documento contém mais informações sobre o conteúdo do log e sua criação.

Pode levar um tempo para que os logs apareçam na sua conta de armazenamento depois de uma ação do Azure Rights Management. A maioria dos logs aparecem dentro de 15 minutos.

A conta de armazenamento que você criou para seus logs de uso do Azure Rights Management é como uma caixa de correio e dá suporte de leitura diretamente da conta de armazenamento, mas não está otimizada para ser usada dessa maneira. Em vez disso, para melhor desempenho e para ajudar a reduzir custos, recomendamos que baixe os logs no armazenamento local, como uma pasta local, um banco de dados, ou um repositório de redução de mapa.

Você pode baixar seus logs de uso de duas maneiras:

-   Use o cmdlet do Windows PowerShell [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx).

    Esse é o modo mais simples de acessar seus logs. Este cmdlet baixa os logs no seu computador, baixando cada blob como um arquivo para um local que você especifique.

-   Use o [SDK do Armazenamento Azure](http://www.windowsazure.com/en-us/develop/net/) para escrever seu próprio aplicativo personalizado para baixar os logs.

    Um aplicativo personalizado pode fornecer mais flexibilidade que o cmdlet Get-AadrmUsageLogs. Por exemplo, você pode querer delegar a descarga de logs a alguém ou a um processo que não deve usar suas credenciais administrativas do Azure Rights Management. Ou, você pode querer sondar os logs em tempo real porque você quer monitorar o uso indevido.

#### Para baixar seus logs de uso usando o PowerShell

-   Inicie o Windows PowerShell com a opção **Executar como administrador** e execute **Get-AadrmUsageLog –Path &lt;location&gt;**. Por exemplo, depois de criar uma pasta chamada **logs** na sua unidade E:

    -   Para baixar todos os logs disponíveis na sua pasta E:\logs: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Para baixar um intervalo específico de blobs: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Quando você execute estes cmdlets, o Windows PowerShell exibe o nome do último blob que foi baixado. Você pode atribuir este nome para uma variável, que lhe permite executar o Get-AadrmUsageLog em um loop ou um trabalho de agendamento, baixando somente os logs incrementais cada vez.

Por exemplo:

**PS C:\&gt; $LastBlobName = Get-AadrmUsageLog –Path "e:\logs"**

**1527**

**PS C:\&gt; $LastBlobName**

**1527**

> [!TIP]
> Você pode agregar todos os arquivos de log baixados em um formato CSV usando o [Log Parser da Microsoft](http://www.microsoft.com/download/details.aspx?id=24659) que é uma ferramenta para converter entre vários formatos de log conhecidos. Você também pode usar esta ferramenta para converter dados para o formato SYSLOG, ou importá-lo em um banco de dados. Depois de instalar a ferramenta, execute **LogParser.exe /?** para obter ajuda e informações para usar essa ferramenta. Por exemplo, você pode executar o seguinte comando para importar todas as informações em um formado de arquivo .log: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

Você pode suspender e retomar o registro em log de uso. Quando você suspende o registro em log, o Azure Rights Management retém as informações de sua conta de armazenamento, de modo que você possa facilmente retomar o registro em log.

#### Para suspender e retomar o registro em log

-   Para suspender o log, use o cmdlet a seguir: [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   Para retomar o log, use o cmdlet a seguir: [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Para verificar se o log está habilitado ou desabilitado, use o cmdlet a seguir: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Um valor de **True** significa que o registro em log de uso está habilitado para o Azure Rights Management e um valor **False** significa que o registro em log está desabilitado.

## <a name="BKMK_ManageStorage"></a>Como gerenciar o armazenamento de log do Azure Rights Management
Você é cobrado pelo espaço de armazenamento que é usado para manter seus logs do Azure Rights Management.

O Azure Rights Management não faz o gerenciamento automático de seus arquivos de log de uso. Se você não executar nenhuma ação, eles permanecerão na sua conta de armazenamento. No entanto, para conservar o espaço e reduzir os custos de armazenamento, você pode querer excluí-los após ter baixado eles. Ou você pode escolher quais arquivos excluir. Com uma exceção, o Azure Rights Management não usa esses arquivos de log, então não há restrições sobre quando você pode excluí-los.

O arquivo que você não deve excluir (ou modificar) é chamado **metadata** que esta no contêiner **rms-metadata**. O Azure Rights Management usa esse blob para controlar o último número de blob que é usado. Se esse arquivo é excluído, o Azure Rights Management inicia um novo contêiner para logs, com um número de blob que começa em 1, e todas as descargas futuras que usem o cmdlet Get-AadrmUsageLog usam esse novo contêiner para baixar os arquivos de log. Como resultado, quaisquer dos logs no contêiner original serão retidos, mas serão órfãos. A única maneira de baixar estes logs órfãos é usando o armazenamento do Azure SDK.

> [!TIP]
> Em vez de você mesmo gerenciar seu armazenamento de log do Azure Rights Management, você pode delegar essa função de gerenciamento a outra empresa, compartilhando seu nome e chave de acesso da conta de armazenamento. Para obter mais informações, consulte a seção [Como delegar acesso a seus logs de uso do Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate) mais adiante neste tópico.

Em algumas circunstâncias, você pode querer regenerar suas chaves de acesso de armazenamento. Por exemplo:

-   Você muda a empresa que gerencia seus logs de uso do Azure Rights Management.

-   Você suspeita que sua chave de acesso de armazenamento está comprometida.

Se isso acontecer com você, isto é quando você usa a chave de acesso secundária (na suposição que você esteve anteriormente usando a chave de acesso primária) para garantir a continuidade do serviço. Quando você regenerar a chave de acesso que você não estava usando previamente, terá que configurar o Azure Rights Management para usar a nova chave. Use o procedimento a seguir para regenerar a chave de acesso secundária e configurar o Azure Rights Management para usá-la:

#### Para regenerar a chave de acesso secundária

1.  Entre no [Portal do Azure](https://portal.azure.com/).

2.  Clique em **Todos os Recursos** e pesquise seu armazenamento, digitando o nome de armazenamento na caixa de texto.

3.  Selecione seu armazenamento e clique em **Configurações**.

4.  Clique no ícone de **Chaves**.

5.  Na seção **Gerenciar chaves**, clique em **Regenerar chave secundária**, clique em Sim para confirmar que deseja regenerar a chave de acesso secundário e copie a nova chave de acesso secundário para a área de transferência.

    Não feche o Portal do Azure.

6.  Inicie o Windows PowerShell com a opção **Executar como administrador** e use o cmdlet [Set-AadrmUsageLogConfig](https://msdn.microsoft.com/library/azure/dn629426.aspx) para que o Azure Rights Management use essa nova chave de acesso, substituindo a *&lt;StorageAccount&gt;* pelo nome da sua conta de armazenamento e a *&lt;Access_Key&gt;* pela chave de acesso secundária regenerada que você acabou de copiar:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > Mesmo que você possa alternar para outra conta de armazenamento quando executa esse comando, esta ação deixa órfãos os logs anteriores e eles não ficam acessíveis para o cmdlet Get-AadrmUsageLogConfig ou comandos e funções de gerenciamento semelhantes.

7.  No Portal do Azure, seção **Gerenciar chaves**, regenere a sua chave de acesso primário.

Para obter mais informações sobre como gerenciar suas chaves de acesso de armazenamento, consulte a seção [Gerenciar suas chaves de acesso de armazenamento](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) em [Sobre contas de armazenamento do Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) na documentação do Azure.

## <a name="BKMK_Delegate"></a>Como delegar acesso a seus logs de uso do Azure Rights Management
Você pode delegar acesso para seus logs do RMS compartilhando seu nome e chave de acesso da conta de armazenamento. Você pode querer delegar acesso para outro usuário administrativo, para um desenvolvedor na sua organização, ou para um fornecedor de software independente (ISV). Como eles não terão suas credenciais de administrador do RMS, eles não podem usar o cmdlet Get-AardrmUsageLog para baixar os registros do RMS. Em vez disso, eles devem usar o Windows Storage SDK para baixar os logs. Como alternativa, eles podem gravar um aplicativo para ler os logs diretamente do Armazenamento do Azure.

É seguro compartilhar seu nome e chave de acesso da conta desta maneira quando a conta de armazenamento é dedicada a seus logs do RMS. Mesmo que outras pessoas tenham sua chave de acesso, eles não podem usá-la para acessar qualquer outra conta de armazenamento ou para usar sua conta de locatário do RMS.

## <a name="BKMK_Interpret"></a>Como interpretar seus logs de uso do Azure Rights Management
Use as informações a seguir para ajudá-lo interpretar os logs de uso do Azure Rights Management.

### O layout da conta de armazenamento
A primeira vez que o Azure Rights Management grava logs para sua conta de armazenamento, ele cria os dois contêiner a seguir:

-   **Rms-metadata**: Esse contêiner é reservado para o Azure Rights Management. Não modifique nem exclua este contêiner.

-   **Rms-logs-&lt;guid&gt;**: Esse contêiner é onde o Azure Rights Management cria e salva os logs. Você pode excluir com segurança qualquer arquivo neste contêiner se você não que mais as informações de log que eles contêm.

Ao longo do tempo, o Azure Rights Management pode criar contêiners **Rms-logs-&lt;guid&gt;** adicionais. Por exemplo, se o contêiner **Rms-metadata** torna-se corrompido ou é acidentalmente excluído, o Azure Rights Management restaura o seu conteúdo e cria um novo contêiner **Rms-logs-&lt;guid&gt;** para todos os logs futuros. Os logs antigos no contêiner antigo não são excluídos mas tornam-se órfãos.

### A sequência de log
O Azure Rights Management grava os logs como uma série de blobs. Cada blob contém um ou mais registros de log, no formato de log W3C estendido.

O nome de cada blob é um número. Dentro de cada contêiner de log o primeiro blob é nomeado 000000001. Cada blob é nomeado sequencialmente na ordem em que ele foi criado. Cada blob contém um ou mais registros de log. Cada registro de log tem um carimbo de hora UTC que indica quando foi servida a solicitação correspondente pelo Azure Rights Management.

> [!IMPORTANT]
> O sistema de registro em log do Azure Rights Management é otimizado para fornecer logs rapidamente, em vez de em ordem sequencial estrita. A ordem dos blobs, assim como a ordem de registros de log em um blob, podem estar fora de sequência cronológica O único motivo pelo qual os blobs são nomeados sequencialmente é para lhe permitir baixá-los incrementalmente com eficiência.
> 
> Dois exemplos de resultados de sequência de log potenciais:
> 
> -   Os registros de log no blob 000000004 podem se sobrepor cronologicamente com os registros de log no blob 000000003. Em casos extremos, todos os registros de log no blob 000000004 podem ter sido gerados antes de todos os registros de log no blob 000000003.
> -   O segundo registro de log em um blob, pode ter sido gerado antes que o primeiro registro de log, mas foi gravado para armazenar em ordem inversa.

Antes que você analise seus logs do Azure Rights Management, recomendamos que baixe e importe o log em um repositório onde você possa classificar os logs com base em seus carimbos de data/hora. Para obter mais informações sobre como baixar os logs, consulte a seção [Como acessar e usar seus logs de uso Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) neste tópico.

Como os logs não são necessariamente cronológicos, mas a maioria deles são gravados dentro de 15 minutos da solicitação, ao identificar os logs que você quer usando seu carimbo de data/hora, adicione 15 minutos na hora em que você estiver interessado. Depois baixe tais logs. Esta estratégia deve assegurar que você consiga quase todos os logs.

Outra coisa para ter em mente é que o carimbo de data/hora em cada registro de log é a hora local do serviço do Azure Rights Management que processa a solicitação. Como o Azure Rights Management é executado em vários servidores entre vários centros de dados, às vezes os logs podem parecer estar fora de sequência, mesmo quando eles são classificados por seu carimbo de data/hora. No entanto, a diferença é pequena e geralmente menor a um minuto. Na maioria dos casos, essa não é uma questão que possa ser um problema para a análise de log.

### O formato de blob
Cada blob está no formato de log estendido W3C. Começa com as duas linhas a seguir:

**#Software: RMS**

**#Version: 1.1**

A primeira linha identifica que esses são os logs do Azure Rights Management. A segunda linha identifica que o resto do blob segue as especificações da versão 1.1. Recomendamos que qualquer aplicativo que analise estes logs verifique estas duas linhas antes de continuar a analisar o resto do blob.

A terceira linha enumera uma lista de nomes do campo que são separados por guias:

**#Fields: data tempo id de linha tipo de solicitação  id de usuário resultado id de correlação id de conteúdo email do proprietário emissor id do modelo nome do arquivo data publicação c-info c-ip**

Cada uma das linhas subsequentes é um registro de log. Os valores dos campos estão na mesma ordem que a linha precedente, e são separados por guias. Use a seguinte tabela para interpretar os campos.

|Nome do campo|Tipo de dados W3C|Descrição|Valor de exemplo|
|-----------------|---------------------|-------------|--------------------|
|date|Data|Data UTC quando a solicitação foi servida.<br /><br />A fonte é o relógio local no servidor que serviu a solicitação.|2013-06-25|
|hora|Hora|Hora UTC no formato de 24 horas quando a solicitação foi servida.<br /><br />A fonte é o relógio local no servidor que serviu a solicitação.|21:59:28|
|row-id|Text|GUID exclusivo para este registro de log.<br /><br />Este valor é usado quando você agrega logs ou cópia logs em um outro formato.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|Nome|Nome do API do RMS que foi solicitado.|AcquireLicense|
|user-id|Cadeia de caracteres|O usuário que fez a solicitação.<br /><br />O valor que é colocado entre aspas simples. Alguns tipos de solicitações são anônimos e, nesse caso, o valor será ”.|‘joe@contoso.com’|
|result|Cadeia de caracteres|‘Êxito’ se a solicitação foi servida com êxito.<br /><br />O tipo de erro entre aspas simples marca se a solicitação falhou.|‘Êxito’|
|correlation-id|Text|O GUID que seja comum entre o log do cliente do RMS e o log do servidor para uma solicitação especificada.<br /><br />Este valor pode ser útil para ajudar a solucionar problemas de clientes.|cab52088-8925-4371-be34-4b71a3112356|
|content-id|Text|O GUID, que se encontra entre chaves que identifica o conteúdo protegido (por exemplo, um documento).<br /><br />Este campo tem um valor somente se o tipo de solicitação é AcquireLicense e é branco par todos os outros tipos de solicitações.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|email proprietário|Cadeia de caracteres|Endereço de email do proprietário do documento.|alice@contoso.com|
|emissor|Cadeia de caracteres|Endereço de email do emissor do documento.|alice@contoso.com (or) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|Id do modelo|Cadeia de caracteres|ID do modelo usado para proteger o documento.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|Nome do arquivo|Cadeia de caracteres|Nome do arquivo do documento que estava protegido.|TopSecretDocument.docx|
|Data de publicação|Data|Data quando o documento foi protegido.|2015-10-15T21:37:00|
|c-info|Cadeia de caracteres|As informações sobre a plataforma do cliente que estão fazendo a solicitação.<br /><br />A cadeia de caracteres varia, dependendo do aplicativo (por exemplo, o sistema operativo ou o navegador).|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|Endereço|O endereço IP do cliente que realiza a solicitação.|64.51.202,144|

#### Exceções para o campo user-id
Mesmo que o campo user-id geralmente indica ao usuário que realizou o pedido, há duas exceções onde o valor não mapeia a um usuário real:

-   O valor **'microsoftrmsonline@&lt;YourTenantID&gt;.rms.&lt;region&gt;.aadrm.com'**.

    Isto indica que um serviço Office 365, como o Exchange Online ou Sharepoint Online, está realizando a solicitação. Na cadeia de caracteres, o *&lt;YourTenantID&gt;* é o GUID para seu locatário e *&lt;region&gt;* é a região onde seu locatário é registrado. Por exemplo, **na** representa América do Norte, **eu** representa a Europa e **ap** representa a Ásia.

-   Se você estiver usando o conector do RMS.

    As solicitações deste conector são registrados em log com o nome principal do serviço que o RMS automaticamente gera quando você instala o conector do RMS.

#### Tipos de solicitações típicas
Há vários tipos de solicitações no Azure Rights Management, mas a seguinte tabela identifica alguns dos tipos de solicitações mais usados.

|Tipo de solicitação|Descrição|
|-----------------------|-------------|
|AcquireLicense|Um cliente de um computador baseado no Windows está solicitando uma licença para conteúdo protegido pelo RMS.|
|AcquirePreLicense|Um cliente, em nome do usuário, está solicitando uma licença para conteúdo protegido pelo RMS.|
|AcquireTemplates|Foi feita uma chamada para adquirir modelos baseados nos IDs de modelo|
|AcquireTemplateInformation|Foi feita uma chamada para obter as identificações do modelo do serviço.|
|AddTemplate|É feita uma chamada do Azure Classic Portal para adicionar um modelo.|
|BECreateEndUserLicenseV1|É feita uma chamada de um dispositivo móvel para criar uma licença de usuário final.|
|BEGetAllTemplatesV1|É feita uma chamada de um dispositivo móvel (backend) para obter todos os modelos.|
|Certify|O cliente certifica o conteúdo para proteção.|
|Decrypt|O cliente está tentando descriptografar o conteúdo protegido pelo RMS.|
|DeleteTemplateById|É feita uma chamada no Azure Classic Portal para excluir um modelo por ID de modelo.|
|ExportTemplateById|É feita uma chamada no Azure Classic Portal para excluir um modelo com base no ID de modelo.|
|FECreateEndUserLicenseV1|Semelhante à solicitação AcquireLicense mas de dispositivos móveis.|
|FECreatePublishingLicenseV1|Igual que o Certify e GetClientLicensorCert juntos, de cliente móveis.|
|FEGetAllTemplates|É feita uma chamada de um dispositivo móvel (frontend) para obter todos os modelos.|
|GetAllTemplates|É feita uma chamada do Azure Classic Portal para obter todos os modelos.|
|GetClientLicensorCert|O cliente está solicitando um certificado de publicação (que é posteriormente usado para proteger conteúdo) de um computador baseado no Windows.|
|GetConfiguration|Um cmdlet do Azure PowerShell é chamado para obter a configuração do locatário do Azure RMS.|
|GetConnectorAuthorizations|É feita uma chamada dos conectores do RMS para obter suas configurações da nuvem.|
|GetTenantFunctionalState|O Azure Classic Portal está verificando se o Azure RMS está ativado.|
|GetTemplateById|É feita uma chamada no Azure Classic Portal para obter um modelo, especificando o ID de modelo.|
|ExportTemplateById|É feita uma chamada no Azure Classic Portal para exportar um modelo, especificando o ID de modelo.|
|FindServiceLocationsForUser|É feita uma chamada para consultas URLs, que é usada para chamar Certify ou AcquireLicense.|
|ImportTemplate|É feita uma chamada do Azure Classic Portal para importar um modelo.|
|ServerCertify|É feita uma chamada de um cliente habilitado para RMS (como SharePoint) para certificar o servidor.|
|SetUsageLogFeatureState|É feita uma chamada para habilitar o registro em log de uso.|
|SetUsageLogStorageAccount|É feita uma chamada para especificar o local dos logs do Azure RMS.|
|SignDigest|É feita uma chamada quando uma chave é usada para fins de assinatura. Isso é chamado geralmente uma vez por AcquireLicence (ou FECreateEndUserLicenseV1), Certify e GetClientLicensorCert (ou FECreatePublishingLicenseV1).|
|UpdateTemplate|É feita uma chamada do Azure Classic Portal para atualizar um modelo existente.|

## <a name="BKMK_PowerShell"></a>Referência do Windows PowerShell
Use os seguintes cmdlets do Windows PowerShell para ter ajuda ao configurar e usar o registro em log de uso do Azure Rights Management:

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Para obter mais informações sobre o Windows PowerShell para Azure Rights Management, consulte [Administrando o Azure Rights Management usando o Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Consulte também
[Usando o Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

