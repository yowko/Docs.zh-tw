---
title: 路由簡介
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: e540e084305aee51d6820cc9ae43f7791d5c07d6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "47058457"
---
# <a name="routing-introduction"></a><span data-ttu-id="a99c0-102">路由簡介</span><span class="sxs-lookup"><span data-stu-id="a99c0-102">Routing Introduction</span></span>
<span data-ttu-id="a99c0-103">路由服務提供了泛型的可外掛式 SOAP 媒介，此媒介能夠根據訊息內容路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="a99c0-104">透過路由服務，您就可以建立複雜路由邏輯，以便實作服務彙總、服務版本控制、優先權路由和多點傳送路由等案例。</span><span class="sxs-lookup"><span data-stu-id="a99c0-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="a99c0-105">路由服務還提供錯誤處理，可讓您設定備份端點清單，當傳送至主要目的端點期間發生錯誤時，訊息就會傳送至此清單中的端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="a99c0-106">這個主題的主要對象為路由服務的新手，內容涵蓋路由服務的基本組態和裝載。</span><span class="sxs-lookup"><span data-stu-id="a99c0-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a99c0-107">組態</span><span class="sxs-lookup"><span data-stu-id="a99c0-107">Configuration</span></span>  
 <span data-ttu-id="a99c0-108">路由服務會實作為 WCF 服務，公開一個或多個從用戶端接收訊息的服務端點，並且將訊息路由傳送至一個或多個目的端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="a99c0-109">服務提供了 <xref:System.ServiceModel.Routing.RoutingBehavior>，它會套用至服務所公開的服務端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="a99c0-110">這個行為可用來設定服務運作方式的各種不同方面。</span><span class="sxs-lookup"><span data-stu-id="a99c0-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="a99c0-111">為了方便使用組態檔進行設定，在指定的參數 **RoutingBehavior**。</span><span class="sxs-lookup"><span data-stu-id="a99c0-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="a99c0-112">在程式碼為基礎的情況下，這些參數會指定為一部分 <xref:System.ServiceModel.Routing.RoutingConfiguration> 物件，然後傳遞至 **RoutingBehavior**。</span><span class="sxs-lookup"><span data-stu-id="a99c0-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="a99c0-113">啟動時，這個行為會將 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> (用來執行訊息的 SOAP 處理) 加入至用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="a99c0-114">這可讓路由服務將訊息傳送至需要不同的端點**MessageVersion**比接收訊息所在的端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="a99c0-115">**RoutingBehavior**也會註冊一個服務延伸， <xref:System.ServiceModel.Routing.RoutingExtension> ，以修改路由服務組態，在執行階段提供了協助工具點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="a99c0-116">**RoutingConfiguration**類別提供一致的方式設定和更新路由服務的組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="a99c0-117">它包含做為路由服務的設定，而用來設定參數**RoutingBehavior**當服務啟動時，或傳遞給**RoutingExtension**修改路由在執行階段組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="a99c0-118">路由邏輯可用來執行訊息的內容架構路由，它是透過將多個 <xref:System.ServiceModel.Dispatcher.MessageFilter> 物件群組為篩選資料表 (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 物件) 的方式定義。</span><span class="sxs-lookup"><span data-stu-id="a99c0-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="a99c0-119">內送訊息會根據包含在篩選資料表，並針對每個訊息篩選條件來評估**MessageFilter**符合訊息，並轉送至目的地端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="a99c0-120">使用指定的篩選資料表，應該用來將訊息路由傳送**RoutingBehavior**組態中，或透過使用程式碼**RoutingConfiguration**物件。</span><span class="sxs-lookup"><span data-stu-id="a99c0-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="a99c0-121">定義端點</span><span class="sxs-lookup"><span data-stu-id="a99c0-121">Defining Endpoints</span></span>  
 <span data-ttu-id="a99c0-122">雖然您似乎應該藉由定義將要使用的路由邏輯開始進行設定，但實際上，您進行的第一個步驟應該是判斷要將訊息路由傳送至其中之端點的組織架構。</span><span class="sxs-lookup"><span data-stu-id="a99c0-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="a99c0-123">路由服務會使用合約定義用來接收和傳送訊息的通道組織結構，因此輸入通道的組織結構必須符合輸出通道的組織結構。</span><span class="sxs-lookup"><span data-stu-id="a99c0-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="a99c0-124">例如，如果您要路由傳送至使用要求-回覆通道組織結構的端點，則必須在傳入端點上使用相容的合約，例如 <xref:System.ServiceModel.Routing.IRequestReplyRouter>。</span><span class="sxs-lookup"><span data-stu-id="a99c0-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="a99c0-125">這表示，如果您的目的端點使用擁有多種通訊模式 (例如混合單向和雙向作業) 的合約，您就無法建立單一服務端點來接收和路由傳送訊息至所有端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="a99c0-126">您必須判斷哪些端點擁有相容的組織結構，並且定義一個或多個服務端點，以便用來接收將路由傳送至目的端點的訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a99c0-127">使用指定多種通訊模式 (例如混合單向和雙向作業) 的合約時，其中一種解決方法，就是在路由服務中使用雙工合約，例如 <xref:System.ServiceModel.Routing.IDuplexSessionRouter>。</span><span class="sxs-lookup"><span data-stu-id="a99c0-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="a99c0-128">不過，這表示繫結必須具備雙工通訊的能力，但這並不適用於所有情況。</span><span class="sxs-lookup"><span data-stu-id="a99c0-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="a99c0-129">在不具備雙工能力的情況下，可能需要將通訊重構為多個端點或修改應用程式。</span><span class="sxs-lookup"><span data-stu-id="a99c0-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="a99c0-130">如需有關路由合約的詳細資訊，請參閱 [路由合約](routing-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="a99c0-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>  
  
 <span data-ttu-id="a99c0-131">定義服務端點之後，您可以使用**RoutingBehavior**關聯特定**RoutingConfiguration**與端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="a99c0-132">使用組態檔設定路由服務時**RoutingBehavior**用來指定篩選資料表，其中包含用來處理此端點上收到的訊息的路由邏輯。</span><span class="sxs-lookup"><span data-stu-id="a99c0-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="a99c0-133">如果您要以程式設計方式設定路由服務可以使用指定的篩選資料表**RoutingConfiguration**。</span><span class="sxs-lookup"><span data-stu-id="a99c0-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="a99c0-134">下列範例會同時以程式設計方式和使用組態檔的方式，定義路由服務使用的服務和用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
```xml  
    <services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 <span data-ttu-id="a99c0-135">這個範例會設定讓路由服務公開 （expose） 單一的端點位址為`http://localhost:8000/routingservice/router`，用來接收要路由傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="a99c0-136">由於訊息會路由傳送至要求-回覆端點，因此服務端點會使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter> 合約。</span><span class="sxs-lookup"><span data-stu-id="a99c0-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="a99c0-137">此設定也會定義單一用戶端端點`http://localhost:8000/servicemodelsample/service`訊息會路由傳送至。</span><span class="sxs-lookup"><span data-stu-id="a99c0-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="a99c0-138">名為"routingTable1"篩選資料表 （未顯示） 包含用來路由訊息的路由邏輯，並使用是與服務端點相關聯**RoutingBehavior** （適用於組態檔） 或**RoutingConfiguration** （適用於以程式設計方式設定）。</span><span class="sxs-lookup"><span data-stu-id="a99c0-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="a99c0-139">路由邏輯</span><span class="sxs-lookup"><span data-stu-id="a99c0-139">Routing Logic</span></span>  
 <span data-ttu-id="a99c0-140">若要定義用來路由傳送訊息的路由邏輯，您必須判斷傳入訊息內包含的哪些資訊可以單獨處理。</span><span class="sxs-lookup"><span data-stu-id="a99c0-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="a99c0-141">例如，如果要路由傳送的所有目的端點共用相同的 SOAP 動作，則訊息內所包含動作的值就不適合做為指標，且訊息不應該路由傳送至該值所指的特定端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="a99c0-142">如果您必須以唯一的方式將訊息路由傳送至某一個特定端點，則應該對唯一識別路由傳送訊息至其中之目的端點的資料進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a99c0-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="a99c0-143">路由服務提供多種**MessageFilter**檢查訊息，例如位址、 動作、 端點名稱或甚至 XPath 查詢中的特定值的實作。</span><span class="sxs-lookup"><span data-stu-id="a99c0-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="a99c0-144">如果這些實作都不符合您的需求，您就可以建立自訂**MessageFilter**實作。</span><span class="sxs-lookup"><span data-stu-id="a99c0-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="a99c0-145">如需訊息篩選條件，並比較使用路由服務所實作的詳細資訊，請參閱[訊息篩選條件](message-filters.md)並[選擇篩選](choosing-a-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="a99c0-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="a99c0-146">多個訊息篩選會組織成篩選資料表，將每個產生關聯**MessageFilter**與目的端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="a99c0-147">此外，篩選資料表還可以選擇性地用來指定備份端點清單，路由服務會在發生傳輸錯誤時，嘗試將訊息路由傳送至這些備份端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="a99c0-148">根據預設，篩選資料表內的所有訊息篩選都會同步評估，不過，您可以指定 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>，讓訊息篩選依照特定順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="a99c0-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="a99c0-149">具有最高優先權的所有項目會先進行評估，而如果在較高優先權層級中找到相符項目，就不會對較低優先權的訊息篩選進行評估。</span><span class="sxs-lookup"><span data-stu-id="a99c0-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="a99c0-150">如需有關篩選資料表的詳細資訊，請參閱[訊息篩選條件](message-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="a99c0-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>  
  
 <span data-ttu-id="a99c0-151">下列範例使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>，它會針對所有訊息評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a99c0-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="a99c0-152">這**MessageFilter**新增至"routingTable1"篩選資料表，其會將**MessageFilter**與名為"CalculatorService"的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="a99c0-153">**RoutingBehavior**然後指定 這個資料表應該用於處理服務端點的路由訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  <span data-ttu-id="a99c0-154">根據預設，路由服務只會評估訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="a99c0-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="a99c0-155">若要讓篩選存取訊息本文，您必須將 <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> 設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a99c0-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="a99c0-156">**多點傳送**</span><span class="sxs-lookup"><span data-stu-id="a99c0-156">**Multicast**</span></span>  
  
 <span data-ttu-id="a99c0-157">雖然許多路由服務組態都使用僅將訊息路由傳送至一個特定端點的獨佔篩選邏輯，但您仍可能需要將特定訊息路由傳送至多個目的端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="a99c0-158">若要將訊息多點傳送至多個目的地，則下列條件必須為 true：</span><span class="sxs-lookup"><span data-stu-id="a99c0-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
-   <span data-ttu-id="a99c0-159">通道組織結構不得為要求-回覆 (但可以是單向或雙工)，因為回應要求的用戶端應用程式只能接收一個回覆。</span><span class="sxs-lookup"><span data-stu-id="a99c0-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
-   <span data-ttu-id="a99c0-160">評估訊息時，必須有多個篩選傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="a99c0-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="a99c0-161">如果這些條件都符合，則訊息會路由傳送至所有評估為 `true` 之篩選的所有端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="a99c0-162">下列範例會定義路由組態，如果訊息中的端點位址路由傳送至這兩個端點會導致 `http://localhost:8000/routingservice/router/rounding` 。</span><span class="sxs-lookup"><span data-stu-id="a99c0-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### <a name="soap-processing"></a><span data-ttu-id="a99c0-163">SOAP 處理</span><span class="sxs-lookup"><span data-stu-id="a99c0-163">SOAP Processing</span></span>  
 <span data-ttu-id="a99c0-164">若要支援不同的通訊協定之間的訊息路由**RoutingBehavior**根據預設會加入<xref:System.ServiceModel.Routing.SoapProcessingBehavior>訊息會路由傳送至的所有用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="a99c0-165">此行為會自動建立新**MessageVersion**之前的訊息路由傳送至端點，以及建立相容**MessageVersion**之前將它以傳回任何回應文件提出要求的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="a99c0-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="a99c0-166">若要建立新的所採取的步驟**MessageVersion**輸出訊息如下所示：</span><span class="sxs-lookup"><span data-stu-id="a99c0-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="a99c0-167">**要求處理**</span><span class="sxs-lookup"><span data-stu-id="a99c0-167">**Request processing**</span></span>  
  
-   <span data-ttu-id="a99c0-168">取得**MessageVersion**的輸出繫結/通道。</span><span class="sxs-lookup"><span data-stu-id="a99c0-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
-   <span data-ttu-id="a99c0-169">取得原始訊息的本文讀取裝置。</span><span class="sxs-lookup"><span data-stu-id="a99c0-169">Get the body reader for the original message.</span></span>  
  
-   <span data-ttu-id="a99c0-170">建立新的訊息使用相同的動作、 本文讀取裝置和新**MessageVersion**。</span><span class="sxs-lookup"><span data-stu-id="a99c0-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
-   <span data-ttu-id="a99c0-171">如果<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>！ = **Addressing.None**，複製 To、 From、 FaultTo 和 RelatesTo 標頭，以新的訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="a99c0-172">將所有訊息屬性複製到新訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-172">Copy all message properties to the new message.</span></span>  
  
-   <span data-ttu-id="a99c0-173">儲存處理回應時要使用的原始要求訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-173">Store the original request message to use when processing the response.</span></span>  
  
-   <span data-ttu-id="a99c0-174">傳回新的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="a99c0-175">**回應處理**</span><span class="sxs-lookup"><span data-stu-id="a99c0-175">**Response processing**</span></span>  
  
-   <span data-ttu-id="a99c0-176">取得**MessageVersion**的原始要求訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-176">Get the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="a99c0-177">取得已接收回應訊息的本文讀取裝置。</span><span class="sxs-lookup"><span data-stu-id="a99c0-177">Get the body reader for the received response message.</span></span>  
  
-   <span data-ttu-id="a99c0-178">建立新的回應訊息與相同的動作、 本文讀取裝置，而**MessageVersion**的原始要求訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="a99c0-179">如果<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>！ = **Addressing.None**，複製 To、 From、 FaultTo 和 RelatesTo 標頭，以新的訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="a99c0-180">將訊息屬性複製到新訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-180">Copy the message properties to the new message.</span></span>  
  
-   <span data-ttu-id="a99c0-181">傳回新的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="a99c0-182">根據預設， **SoapProcessingBehavior**會自動新增至用戶端端點<xref:System.ServiceModel.Routing.RoutingBehavior>在服務啟動時; 不過，您可以控制是否 SOAP 處理加入至所有用戶端端點所使用<xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a99c0-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="a99c0-183">如果需要對 SOAP 處理進行更細微的控制，您也可以將此行為直接加入至特定端點，並且在端點層級啟用或停用此行為。</span><span class="sxs-lookup"><span data-stu-id="a99c0-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a99c0-184">如果端點需要與原始要求訊息不同的 MessageVersion，且該端點的 SOAP 處理已停用，則您必須提供自訂機制來處理任何必要的 SOAP 修改，才能將訊息傳送至目的端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="a99c0-185">在下列範例中， **soapProcessingEnabled**屬性用來防止**SoapProcessingBehavior**自動新增至所有用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="a99c0-186">動態組態</span><span class="sxs-lookup"><span data-stu-id="a99c0-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="a99c0-187">當您加入其他用戶端端點，或是需要修改用來路由傳送訊息的篩選時，必須能夠在執行階段動態更新組態，以避免中斷目前正透過路由服務接收訊息的端點服務。</span><span class="sxs-lookup"><span data-stu-id="a99c0-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="a99c0-188">修改組態檔或主應用程式的程式碼不一定足夠，因為這兩種方法都需要回收應用程式，而這樣可能會導致目前正在傳輸的任何訊息遺失，且在等待服務重新啟動時可能發生停機。</span><span class="sxs-lookup"><span data-stu-id="a99c0-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="a99c0-189">您只能修改**RoutingConfiguration**以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="a99c0-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="a99c0-190">雖然您一開始可以使用組態檔設定服務，您只能修改組態，在執行階段透過建構新**RoutingConfigution**並將它傳遞做為參數<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A>方法由<xref:System.ServiceModel.Routing.RoutingExtension>服務延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a99c0-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfigution** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="a99c0-191">目前正在傳輸的任何訊息會繼續使用先前的設定，在呼叫之後收到的訊息時，路由傳送**ApplyConfiguration**使用新的組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="a99c0-192">下列範例示範建立路由服務的執行個體，然後修改組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  <span data-ttu-id="a99c0-193">使用這個方式更新路由服務時，只能傳遞新組態，</span><span class="sxs-lookup"><span data-stu-id="a99c0-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="a99c0-194">而無法只修改目前組態的選取項目 (Element)，或是附加新項目 (Item) 至目前組態；您必須建立和傳遞取代現有組態的新組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a99c0-195">使用舊組態開啟的任何工作階段都會繼續使用舊組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="a99c0-196">只有新的工作階段才會使用新組態。</span><span class="sxs-lookup"><span data-stu-id="a99c0-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="a99c0-197">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="a99c0-197">Error Handling</span></span>  
 <span data-ttu-id="a99c0-198">如果嘗試傳送訊息時發生任何 <xref:System.ServiceModel.CommunicationException>，則會進行錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a99c0-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="a99c0-199">這些例外狀況通常表示，嘗試與定義的用戶端端點 (如 <xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException> 或 <xref:System.ServiceModel.CommunicationObjectFaultedException>) 進行通訊時發生問題。</span><span class="sxs-lookup"><span data-stu-id="a99c0-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="a99c0-200">錯誤處理程式碼也會攔截並嘗試重新傳送的時機<xref:System.TimeoutException>發生時，這是另一個常見的例外狀況不衍生自**CommunicationException**。</span><span class="sxs-lookup"><span data-stu-id="a99c0-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="a99c0-201">發生上述其中一個例外狀況時，路由服務會容錯移轉至備份端點清單。</span><span class="sxs-lookup"><span data-stu-id="a99c0-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="a99c0-202">如果所有備份端點都發生通訊錯誤而失敗，或是某個端點傳回例外狀況，表示目的端服務內發生錯誤，則路由服務會將錯誤傳回至用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="a99c0-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a99c0-203">錯誤處理功能會擷取並處理嘗試傳送訊息和嘗試關閉通道時發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a99c0-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="a99c0-204">錯誤處理程式碼不是偵測或處理它與其進行通訊的應用程式端點所建立的例外狀況<xref:System.ServiceModel.FaultException>所擲回一項服務會出現在路由服務的身分**FaultMessage**並且送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="a99c0-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="a99c0-205">如果路由服務嘗試回覆訊息時發生錯誤，您可能會在用戶端收到 <xref:System.ServiceModel.FaultException>，而非路由服務不存在時通常會收到的 <xref:System.ServiceModel.EndpointNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="a99c0-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="a99c0-206">路由服務可能會因而遮蓋例外狀況，而且除非您檢查巢狀例外狀況，否則無法提供完整透明度。</span><span class="sxs-lookup"><span data-stu-id="a99c0-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="a99c0-207">追蹤例外狀況</span><span class="sxs-lookup"><span data-stu-id="a99c0-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="a99c0-208">當傳送訊息至清單中的端點失敗，路由服務會追蹤產生的例外狀況資料，並附加為一個名為的訊息屬性的例外狀況詳細資料**例外狀況**。</span><span class="sxs-lookup"><span data-stu-id="a99c0-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="a99c0-209">如此可保留例外狀況資料，並且讓使用者透過訊息偵測器，以程式設計方式進行存取。</span><span class="sxs-lookup"><span data-stu-id="a99c0-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="a99c0-210">例外狀況資料是以一個訊息為單位儲存在字典中，該字典會將端點名稱對應至嘗試傳送訊息時發生的例外狀況詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a99c0-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="a99c0-211">備份端點</span><span class="sxs-lookup"><span data-stu-id="a99c0-211">Backup Endpoints</span></span>  
 <span data-ttu-id="a99c0-212">篩選資料表中的每一個篩選項目都可以選擇性地指定備份端點清單，這些端點會在傳送至主要端點發生傳輸錯誤時使用。</span><span class="sxs-lookup"><span data-stu-id="a99c0-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="a99c0-213">如果發生這類錯誤，路由服務會嘗試將訊息傳送至備份端點清單中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="a99c0-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="a99c0-214">如果此傳送嘗試同樣發生傳輸錯誤，則會嘗試備份清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="a99c0-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="a99c0-215">路由服務會繼續將訊息傳送至清單中的每一個端點，直到訊息接收成功、所有端點都傳回傳輸錯誤，或是端點傳回非傳輸錯誤為止。</span><span class="sxs-lookup"><span data-stu-id="a99c0-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="a99c0-216">下列範例設定讓路由服務使用備份清單。</span><span class="sxs-lookup"><span data-stu-id="a99c0-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### <a name="supported-error-patterns"></a><span data-ttu-id="a99c0-217">支援的錯誤模式</span><span class="sxs-lookup"><span data-stu-id="a99c0-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="a99c0-218">下表說明與使用備份端點清單相容的模式，以及說明特定模式之錯誤處理詳細資料的附註。</span><span class="sxs-lookup"><span data-stu-id="a99c0-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="a99c0-219">模式</span><span class="sxs-lookup"><span data-stu-id="a99c0-219">Pattern</span></span>|<span data-ttu-id="a99c0-220">工作階段</span><span class="sxs-lookup"><span data-stu-id="a99c0-220">Session</span></span>|<span data-ttu-id="a99c0-221">異動</span><span class="sxs-lookup"><span data-stu-id="a99c0-221">Transaction</span></span>|<span data-ttu-id="a99c0-222">接收內容</span><span class="sxs-lookup"><span data-stu-id="a99c0-222">Receive Context</span></span>|<span data-ttu-id="a99c0-223">支援的備份清單</span><span class="sxs-lookup"><span data-stu-id="a99c0-223">Backup List Supported</span></span>|<span data-ttu-id="a99c0-224">備註</span><span class="sxs-lookup"><span data-stu-id="a99c0-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="a99c0-225">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-225">One-Way</span></span>||||<span data-ttu-id="a99c0-226">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-226">Yes</span></span>|<span data-ttu-id="a99c0-227">嘗試在備份端點上重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="a99c0-228">如果此訊息為多點傳送，則只有在失敗通道上的訊息會移到備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="a99c0-229">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-229">One-Way</span></span>||<span data-ttu-id="a99c0-230">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-230">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="a99c0-231">否</span><span class="sxs-lookup"><span data-stu-id="a99c0-231">No</span></span>|<span data-ttu-id="a99c0-232">擲回例外狀況，且交易會復原。</span><span class="sxs-lookup"><span data-stu-id="a99c0-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="a99c0-233">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-233">One-Way</span></span>|||<span data-ttu-id="a99c0-234">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-234">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-235">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-235">Yes</span></span>|<span data-ttu-id="a99c0-236">嘗試在備份端點上重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="a99c0-237">成功接收訊息之後，完成所有接收內容。</span><span class="sxs-lookup"><span data-stu-id="a99c0-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="a99c0-238">如果任何端點未成功接收訊息，則不會完成接收內容。</span><span class="sxs-lookup"><span data-stu-id="a99c0-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="a99c0-239">如果此訊息為多點傳送，則至少有一個端點 (主要或備份) 成功接收訊息才會完成接收內容。</span><span class="sxs-lookup"><span data-stu-id="a99c0-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="a99c0-240">如果任何多點傳送路徑中沒有任何端點成功接收訊息，則不會完成接收內容。</span><span class="sxs-lookup"><span data-stu-id="a99c0-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="a99c0-241">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-241">One-Way</span></span>||<span data-ttu-id="a99c0-242">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-242">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-243">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-243">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-244">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-244">Yes</span></span>|<span data-ttu-id="a99c0-245">中止之前的交易、建立新交易，然後重新傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="a99c0-246">發生錯誤的訊息會傳送至備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="a99c0-247">建立其中所有傳輸都成功的交易之後，完成接收內容並認可交易。</span><span class="sxs-lookup"><span data-stu-id="a99c0-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="a99c0-248">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-248">One-Way</span></span>|<span data-ttu-id="a99c0-249">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-249">![Check mark](media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="a99c0-250">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-250">Yes</span></span>|<span data-ttu-id="a99c0-251">嘗試在備份端點上重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="a99c0-252">在多點傳送的情況下，只有在發生錯誤之工作階段中的訊息，或是工作階段關閉失敗之工作階段中的訊息，才會重新傳送至備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="a99c0-253">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-253">One-Way</span></span>|<span data-ttu-id="a99c0-254">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-254">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-255">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-255">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="a99c0-256">否</span><span class="sxs-lookup"><span data-stu-id="a99c0-256">No</span></span>|<span data-ttu-id="a99c0-257">擲回例外狀況，且交易會復原。</span><span class="sxs-lookup"><span data-stu-id="a99c0-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="a99c0-258">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-258">One-Way</span></span>|<span data-ttu-id="a99c0-259">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-259">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="a99c0-260">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-260">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-261">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-261">Yes</span></span>|<span data-ttu-id="a99c0-262">嘗試在備份端點上重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="a99c0-263">所有訊息傳送完成且未發生錯誤之後，工作階段會指出沒有其他訊息，且路由服務成功關閉所有傳出工作階段通道，所有接收內容都已完成，以及傳入工作階段通道已關閉。</span><span class="sxs-lookup"><span data-stu-id="a99c0-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="a99c0-264">單向</span><span class="sxs-lookup"><span data-stu-id="a99c0-264">One-Way</span></span>|<span data-ttu-id="a99c0-265">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-265">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-266">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-266">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-267">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-267">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-268">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-268">Yes</span></span>|<span data-ttu-id="a99c0-269">中止目前的交易，並且建立新交易。</span><span class="sxs-lookup"><span data-stu-id="a99c0-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="a99c0-270">重新傳送工作階段中所有之前的訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="a99c0-271">建立其中所有訊息已成功送出的交易，且工作階段指出沒有其他訊息之後，所有傳出工作階段通道都會關閉、交易的接收內容會全部完成、傳入工作階段通道會關閉，並且會認可交易。</span><span class="sxs-lookup"><span data-stu-id="a99c0-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="a99c0-272">在多點傳送訊息的情況下，未發生錯誤的訊息會如以往重新傳送至相同的目的地，而發生錯誤的訊息則會傳送至備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="a99c0-273">雙向</span><span class="sxs-lookup"><span data-stu-id="a99c0-273">Two-Way</span></span>||||<span data-ttu-id="a99c0-274">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-274">Yes</span></span>|<span data-ttu-id="a99c0-275">傳送至備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-275">Send to a backup destination.</span></span>  <span data-ttu-id="a99c0-276">通道傳回回應訊息之後，將回應傳回至原始用戶端。</span><span class="sxs-lookup"><span data-stu-id="a99c0-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="a99c0-277">雙向</span><span class="sxs-lookup"><span data-stu-id="a99c0-277">Two-Way</span></span>|<span data-ttu-id="a99c0-278">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-278">![Check mark](media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="a99c0-279">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-279">Yes</span></span>|<span data-ttu-id="a99c0-280">將通道上的所有訊息傳送至備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="a99c0-281">通道傳回回應訊息之後，將回應傳回至原始用戶端。</span><span class="sxs-lookup"><span data-stu-id="a99c0-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="a99c0-282">雙向</span><span class="sxs-lookup"><span data-stu-id="a99c0-282">Two-Way</span></span>||<span data-ttu-id="a99c0-283">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-283">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="a99c0-284">否</span><span class="sxs-lookup"><span data-stu-id="a99c0-284">No</span></span>|<span data-ttu-id="a99c0-285">擲回例外狀況，且交易會復原。</span><span class="sxs-lookup"><span data-stu-id="a99c0-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="a99c0-286">雙向</span><span class="sxs-lookup"><span data-stu-id="a99c0-286">Two-Way</span></span>|<span data-ttu-id="a99c0-287">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-287">![Check mark](media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="a99c0-288">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-288">![Check mark](media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="a99c0-289">否</span><span class="sxs-lookup"><span data-stu-id="a99c0-289">No</span></span>|<span data-ttu-id="a99c0-290">擲回例外狀況，且交易會復原。</span><span class="sxs-lookup"><span data-stu-id="a99c0-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="a99c0-291">雙工</span><span class="sxs-lookup"><span data-stu-id="a99c0-291">Duplex</span></span>||||<span data-ttu-id="a99c0-292">否</span><span class="sxs-lookup"><span data-stu-id="a99c0-292">No</span></span>|<span data-ttu-id="a99c0-293">目前不支援非工作階段雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="a99c0-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="a99c0-294">雙工</span><span class="sxs-lookup"><span data-stu-id="a99c0-294">Duplex</span></span>|<span data-ttu-id="a99c0-295">![核取記號](media/checkmark.gif "核取記號")</span><span class="sxs-lookup"><span data-stu-id="a99c0-295">![Check mark](media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="a99c0-296">是</span><span class="sxs-lookup"><span data-stu-id="a99c0-296">Yes</span></span>|<span data-ttu-id="a99c0-297">傳送至備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a99c0-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="a99c0-298">裝載</span><span class="sxs-lookup"><span data-stu-id="a99c0-298">Hosting</span></span>  
 <span data-ttu-id="a99c0-299">由於路由服務會當做 WCF 服務實作，因此必須在應用程式內自我裝載或是由 IIS 或 WAS 裝載。</span><span class="sxs-lookup"><span data-stu-id="a99c0-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="a99c0-300">建議您在 IIS、WAS 或 Windows 服務應用程式中裝載路由服務，以便利用這些裝載環境中提供的自動啟動和生命週期管理功能。</span><span class="sxs-lookup"><span data-stu-id="a99c0-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="a99c0-301">下列範例示範在應用程式中裝載路由服務。</span><span class="sxs-lookup"><span data-stu-id="a99c0-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="a99c0-302">若要在 IIS 或 WAS 內裝載路由服務，您必須建立服務檔案 (.svc) 或使用服務的組態架構啟動。</span><span class="sxs-lookup"><span data-stu-id="a99c0-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="a99c0-303">使用服務檔案時，必須使用 Service 參數指定 <xref:System.ServiceModel.Routing.RoutingService>。</span><span class="sxs-lookup"><span data-stu-id="a99c0-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="a99c0-304">下列範例包含範例服務檔案，可用來將路由服務裝載於 IIS 或 WAS。</span><span class="sxs-lookup"><span data-stu-id="a99c0-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="a99c0-305">路由服務與模擬</span><span class="sxs-lookup"><span data-stu-id="a99c0-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="a99c0-306">WCF 路由服務可以搭配模擬使用以傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="a99c0-307">平常對模擬的所有 Windows 條件約束在這裡都適用。</span><span class="sxs-lookup"><span data-stu-id="a99c0-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="a99c0-308">當您撰寫您自己的服務時，如果需要設定服務或帳戶使用權限以使用模擬，就必須執行那些同樣的步驟來搭配路由服務使用模擬。</span><span class="sxs-lookup"><span data-stu-id="a99c0-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="a99c0-309">如需詳細資訊，請參閱 <<c0> [ 委派和模擬](delegation-and-impersonation-with-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="a99c0-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="a99c0-310">搭配路由服務的模擬需要使用 ASP.NET 模擬 (採用 ASP.NET 相容模式時) 或 Windows 認證 (這已設定為允許模擬)。</span><span class="sxs-lookup"><span data-stu-id="a99c0-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="a99c0-311">如需有關 ASP.NET 相容性模式的詳細資訊，請參閱[WCF 服務與 ASP.NET](wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="a99c0-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a99c0-312">WCF 路由服務不支援基本驗證的模擬。</span><span class="sxs-lookup"><span data-stu-id="a99c0-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="a99c0-313">若要搭配路由服務使用 ASP.NET 模擬，請在服務裝載環境中啟用 ASP.NET 相容模式。</span><span class="sxs-lookup"><span data-stu-id="a99c0-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="a99c0-314">路由服務已經標記為允許 ASP.NET 相容模式，將會自動啟用模擬。</span><span class="sxs-lookup"><span data-stu-id="a99c0-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="a99c0-315">ASP.NET 與路由服務整合時，模擬是唯一受支援的使用方式。</span><span class="sxs-lookup"><span data-stu-id="a99c0-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="a99c0-316">若要搭配路由服務使用 Windows 認證模擬，您必須同時設定認證與服務。</span><span class="sxs-lookup"><span data-stu-id="a99c0-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="a99c0-317">用戶端認證物件 (<xref:System.ServiceModel.Security.WindowsClientCredential>，可從 <xref:System.ServiceModel.ChannelFactory> 中存取) 定義允許模擬所必須設定的 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="a99c0-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="a99c0-318">最後，您必須在服務上設定 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 行為，才能將 `ImpersonateCallerForAllOperations` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a99c0-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="a99c0-319">路由服務會使用這個旗標決定是否要建立用戶端，用來轉送已啟用模擬的訊息。</span><span class="sxs-lookup"><span data-stu-id="a99c0-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99c0-320">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a99c0-320">See Also</span></span>  
 [<span data-ttu-id="a99c0-321">訊息篩選</span><span class="sxs-lookup"><span data-stu-id="a99c0-321">Message Filters</span></span>](message-filters.md)  
 [<span data-ttu-id="a99c0-322">路由合約</span><span class="sxs-lookup"><span data-stu-id="a99c0-322">Routing Contracts</span></span>](routing-contracts.md)  
 [<span data-ttu-id="a99c0-323">選擇篩選</span><span class="sxs-lookup"><span data-stu-id="a99c0-323">Choosing a Filter</span></span>](choosing-a-filter.md)
