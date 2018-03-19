---
title: "HOW TO：使用篩選"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94d45537ca3edd5f31f1ed31898857f002312a0b
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-filters"></a><span data-ttu-id="f17c6-102">HOW TO：使用篩選</span><span class="sxs-lookup"><span data-stu-id="f17c6-102">How To: Use Filters</span></span>
<span data-ttu-id="f17c6-103">本主題概要說明建立使用多個篩選條件之路由組態所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="f17c6-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="f17c6-104">在此範例中，會將訊息路由至計算機服務的兩種實作 (regularCalc 與 roundingCalc)。</span><span class="sxs-lookup"><span data-stu-id="f17c6-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="f17c6-105">兩項實作都支援相同的作業，不過其中一個服務會在傳回之前將所有的計算結果四捨五入至最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="f17c6-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="f17c6-106">用戶端應用程式必須能夠指出是否要使用四捨五入後的服務版本，如果未指定任何服務偏好設定，則會在兩項服務之間平衡訊息負載。</span><span class="sxs-lookup"><span data-stu-id="f17c6-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="f17c6-107">由這兩項服務公開的作業為：</span><span class="sxs-lookup"><span data-stu-id="f17c6-107">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="f17c6-108">Add</span><span class="sxs-lookup"><span data-stu-id="f17c6-108">Add</span></span>  
  
-   <span data-ttu-id="f17c6-109">Subtract</span><span class="sxs-lookup"><span data-stu-id="f17c6-109">Subtract</span></span>  
  
-   <span data-ttu-id="f17c6-110">乘法</span><span class="sxs-lookup"><span data-stu-id="f17c6-110">Multiply</span></span>  
  
-   <span data-ttu-id="f17c6-111">Divide</span><span class="sxs-lookup"><span data-stu-id="f17c6-111">Divide</span></span>  
  
 <span data-ttu-id="f17c6-112">由於兩項服務皆實作同一個作業，因此您不能使用 [動作] 篩選條件，因為訊息中指定的動作不會是唯一的動作。</span><span class="sxs-lookup"><span data-stu-id="f17c6-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="f17c6-113">相反的，您必須進行額外的工作，以確保訊息能夠路由至正確的端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="f17c6-114">若要判斷唯一資料</span><span class="sxs-lookup"><span data-stu-id="f17c6-114">Determine Unique Data</span></span>  
  
1.  <span data-ttu-id="f17c6-115">因為這兩項服務實作會處理相同的作業，而且它們與不是由其傳回的資料完全相同，所以包含在來自用戶端應用程式之訊息中的基底資料的唯一性質不足，無法藉此判斷路由要求方式。</span><span class="sxs-lookup"><span data-stu-id="f17c6-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="f17c6-116">但是，如果用戶端應用程式在訊息中加入唯一的標頭值，您就可以利用這個值來判斷訊息的路由方式。</span><span class="sxs-lookup"><span data-stu-id="f17c6-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="f17c6-117">在這個範例中，如果用戶端應用程式需要由四捨五入計算機來處理訊息，就會使用下列程式碼加入自訂的標頭：</span><span class="sxs-lookup"><span data-stu-id="f17c6-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="f17c6-118">您現在可以使用 XPath 篩選條件在訊息中檢查這個標頭，並且將包含標頭的訊息路由至 roundCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="f17c6-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2.  <span data-ttu-id="f17c6-119">此外，路由服務會公開兩個虛擬服務端點，這兩個端點可以搭配使用 EndpointName、EndpointAddress 或 PrefixEndpointAddress 篩選條件，根據用戶端應用程式送出要求的目的地端點，透過唯一的方式將傳入訊息路由至特定的計算機實作。</span><span class="sxs-lookup"><span data-stu-id="f17c6-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="f17c6-120">若要定義端點</span><span class="sxs-lookup"><span data-stu-id="f17c6-120">Define Endpoints</span></span>  
  
1.  <span data-ttu-id="f17c6-121">定義路由服務所使用的端點時，應該先判斷用戶端及服務所採用的通道型別。</span><span class="sxs-lookup"><span data-stu-id="f17c6-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="f17c6-122">在此案例中，兩個目的地服務皆使用要求-回覆模式，因此會使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter>。</span><span class="sxs-lookup"><span data-stu-id="f17c6-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="f17c6-123">下列範例定義路由服務所公開的服務端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="f17c6-124">路由服務會使用這個組態公開三個獨立的端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="f17c6-125">視執行階段選擇而定，用戶端應用程式會將訊息傳送至其中一個位址。</span><span class="sxs-lookup"><span data-stu-id="f17c6-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="f17c6-126">送達其中一個 （"rounding/calculator"或"regular/calculator"） 的 「 虛擬 」 服務端點的訊息都會轉送到對應的計算機實作。</span><span class="sxs-lookup"><span data-stu-id="f17c6-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="f17c6-127">如果用戶端應用程式不將要求傳送至特定的端點，訊息就會以一般端點為對象。</span><span class="sxs-lookup"><span data-stu-id="f17c6-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="f17c6-128">無論選擇何種端點，用戶端應用程式都可以選擇加入自訂標頭，表示應將訊息轉送至四捨五入計算機實作。</span><span class="sxs-lookup"><span data-stu-id="f17c6-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2.  <span data-ttu-id="f17c6-129">下列範例定義路由服務用來路由訊息的用戶端 (目的地) 端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="f17c6-130">篩選資料表中會使用這些端點表示訊息符合特定篩選條件時會送達的目的地端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="f17c6-131">若要定義篩選條件</span><span class="sxs-lookup"><span data-stu-id="f17c6-131">Define Filters</span></span>  
  
1.  <span data-ttu-id="f17c6-132">若要將根據用戶端應用程式加入至訊息的"RoundingCalculator"自訂標頭的訊息路由，定義使用 XPath 查詢檢查此標頭存在的篩選。</span><span class="sxs-lookup"><span data-stu-id="f17c6-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="f17c6-133">因為此標頭利用自訂命名空間定義，也會加入可在 XPath 查詢中定義的 「 自訂 」 所使用的自訂命名空間前置詞的命名空間項目。</span><span class="sxs-lookup"><span data-stu-id="f17c6-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="f17c6-134">下列範例定義必要的路由區段、命名空間資料表，以及 XPath 篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="f17c6-135">這**MessageFilter**尋找 RoundingCalculator 標頭中包含"rounding"值的訊息。</span><span class="sxs-lookup"><span data-stu-id="f17c6-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="f17c6-136">這個標頭是由用戶端設定的，用於指出應將訊息路由至 roundingCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="f17c6-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f17c6-137">S12 命名空間前置詞為預設會在命名空間資料表，且代表命名空間"http://www.w3.org/2003/05/soap-envelope"。</span><span class="sxs-lookup"><span data-stu-id="f17c6-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
2.  <span data-ttu-id="f17c6-138">您必須同時設定會尋找兩個虛擬端點上接收到之訊息的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="f17c6-139">第一個虛擬端點是"regular/calculator"端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="f17c6-140">用戶端可以將要求傳送至這個端點，指出應將訊息路由至 regularCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="f17c6-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="f17c6-141">下列組態定義的篩選條件會使用 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>，判斷訊息是否透過具有 filterData 中指定之名稱的端點送達。</span><span class="sxs-lookup"><span data-stu-id="f17c6-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="f17c6-142">如果名為"calculatorEndpoint"的服務端點所接收訊息時，此篩選條件會評估為`true`。</span><span class="sxs-lookup"><span data-stu-id="f17c6-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3.  <span data-ttu-id="f17c6-143">接下來，需要定義的篩選條件會尋找傳送至 roundingEndpoint 的位址之訊息。</span><span class="sxs-lookup"><span data-stu-id="f17c6-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="f17c6-144">用戶端可以將要求傳送至這個端點，指出應將訊息路由至 roundingCalc 服務。</span><span class="sxs-lookup"><span data-stu-id="f17c6-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="f17c6-145">下列設定會定義使用的篩選條件<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>來判斷訊息是否送達"rounding/calculator"端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="f17c6-146">如果以"http://localhost/routingservice/router/rounding/"開頭的位址在收到訊息，則此篩選條件評估為**true**。</span><span class="sxs-lookup"><span data-stu-id="f17c6-146">If a message is received at an address that begins with "http://localhost/routingservice/router/rounding/" then this filter evaluates to **true**.</span></span> <span data-ttu-id="f17c6-147">由於此組態使用的基底位址就是 「 http://localhost/routingservice/router"而 roundingEndpoint 的指定的位址是"rounding/calculator"，用來與此端點通訊的完整位址是"http://localhost/routingservice/路由器/rounding/calculator"，符合此篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-147">Because the base address used by this configuration is "http://localhost/routingservice/router" and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is "http://localhost/routingservice/router/rounding/calculator", which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f17c6-148">PrefixEndpointAddress 篩選條件執行比對時不會評估主機名稱，因為可以使用多種主機名稱 (均為從用戶端應用程式參考主機的有效方式) 參考單一主機。</span><span class="sxs-lookup"><span data-stu-id="f17c6-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="f17c6-149">例如，下列所有名稱皆可參考同一個主機：</span><span class="sxs-lookup"><span data-stu-id="f17c6-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    >  -   <span data-ttu-id="f17c6-150">localhost</span><span class="sxs-lookup"><span data-stu-id="f17c6-150">localhost</span></span>  
    > -   <span data-ttu-id="f17c6-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="f17c6-151">127.0.0.1</span></span>  
    > -   <span data-ttu-id="f17c6-152">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="f17c6-152">www.contoso.com</span></span>  
    > -   <span data-ttu-id="f17c6-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="f17c6-153">ContosoWeb01</span></span>  
  
4.  <span data-ttu-id="f17c6-154">最終的篩選條件必須支援路由送達一般端點 (沒有自訂標頭) 的訊息。</span><span class="sxs-lookup"><span data-stu-id="f17c6-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="f17c6-155">在這個案例中，訊息應在 regularCalc 和 roundingCalc 服務之間交替。</span><span class="sxs-lookup"><span data-stu-id="f17c6-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="f17c6-156">若要支援這些訊息的 「 循環配置資源 」 路由，使用自訂的篩選器可讓一個篩選條件執行個體，以符合每個訊息處理。</span><span class="sxs-lookup"><span data-stu-id="f17c6-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="f17c6-157">下列內容定義 RoundRobinMessageFilter 的兩個執行個體，這些執行個體群組在一起，表示應在彼此之間交替。</span><span class="sxs-lookup"><span data-stu-id="f17c6-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="f17c6-158">在執行階段時期，這個篩選條件類型會在所有已定義的此類型篩選執行個體之間交替 (這些執行個體已設定在一個集合的相同群組中)。</span><span class="sxs-lookup"><span data-stu-id="f17c6-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="f17c6-159">這樣可讓由這個自訂篩選條件處理的訊息在針對 RoundRobinFilter1 和 RoundRobinFilter2 傳回 `true` 之間交替。</span><span class="sxs-lookup"><span data-stu-id="f17c6-159">This causes messages processed by this custom filter to alternate between returning `true` for RoundRobinFilter1 and RoundRobinFilter2.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="f17c6-160">若要定義篩選資料表</span><span class="sxs-lookup"><span data-stu-id="f17c6-160">Define Filter Tables</span></span>  
  
1.  <span data-ttu-id="f17c6-161">若要將篩選條件與特定用戶端端點產生關聯，您必須將這些篩選條件置於篩選資料表中。</span><span class="sxs-lookup"><span data-stu-id="f17c6-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="f17c6-162">此範例案例也使用篩選條件優先順序設定，這是選擇性的設定，可讓您指出處理篩選條件的順序。</span><span class="sxs-lookup"><span data-stu-id="f17c6-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="f17c6-163">如果未指定篩選條件的優先順序，就會同時評估所有篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f17c6-164">指定篩選條件優先順序可以讓您控制處理篩選條件的順序，但這麼做可能會對路由服務的效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="f17c6-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="f17c6-165">如果可行，請建構使用不需篩選條件優先順序的篩選條件邏輯。</span><span class="sxs-lookup"><span data-stu-id="f17c6-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="f17c6-166">下列範例定義篩選資料表並加入至具有優先順序為 2 的資料表先前定義的"XPathFilter"。</span><span class="sxs-lookup"><span data-stu-id="f17c6-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="f17c6-167">這個項目也指定是否"XPathFilter"符合訊息，訊息會路由至"roundingCalcEndpoint"</span><span class="sxs-lookup"><span data-stu-id="f17c6-167">This entry also specifies that if the "XPathFilter" matches the message, the message will be routed to the "roundingCalcEndpoint"</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="f17c6-168">如果指定篩選條件優先順序，會先評估優先順序最高的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="f17c6-169">如果有一個或多個屬於特定優先順序層級的篩選條件相符，則不會評估優先順序層級較低的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="f17c6-170">在此案例中，2 是所指定的最高優先順序，也是這個層級唯一的篩選條件項目。</span><span class="sxs-lookup"><span data-stu-id="f17c6-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2.  <span data-ttu-id="f17c6-171">定義篩選條件項目是為了檢查端點名稱或位址前置詞，以確定特定端點是否已收到訊息。</span><span class="sxs-lookup"><span data-stu-id="f17c6-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="f17c6-172">下列項目會將這兩種篩選條件項目都加入到篩選資料表中，並且將它們與訊息的路由目的地端點產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f17c6-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="f17c6-173">這些篩選條件的優先順序皆設定為 1，表示只有在前一個 XPath 篩選條件與訊息不相符時，這些篩選條件才能執行。</span><span class="sxs-lookup"><span data-stu-id="f17c6-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="f17c6-174">由於這些篩選條件的優先順序為 1，因此只有在優先順序層級 2 的篩選條件與訊息不相符時，才會評估這些篩選條件。</span><span class="sxs-lookup"><span data-stu-id="f17c6-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="f17c6-175">同時，由於兩種篩選條件的優先順序層級相同，因此會同時評估。</span><span class="sxs-lookup"><span data-stu-id="f17c6-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="f17c6-176">兩個篩選條件彼此互斥，所以只有其中一個會與訊息相符。</span><span class="sxs-lookup"><span data-stu-id="f17c6-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3.  <span data-ttu-id="f17c6-177">如果訊息不符合之前的所有篩選條件，就會透過泛型服務端點接收訊息，而且不會包含指出路由目的地的標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="f17c6-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="f17c6-178">這些訊息會由自訂篩選條件處理，此篩選條件會在兩項計算機服務之間平衡這些訊息的負載。</span><span class="sxs-lookup"><span data-stu-id="f17c6-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="f17c6-179">下列範例示範如何在篩選資料表中加入篩選條件項目，其中每個篩選條件均與兩個目的地端點的其中之一產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f17c6-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="f17c6-180">由於這些項目指定優先順序 0，因此只有在優先順序較高的篩選條件均與訊息不相符時，才會評估這些項目。</span><span class="sxs-lookup"><span data-stu-id="f17c6-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="f17c6-181">同時，由於兩種項目的優先順序相同，因此會同時評估。</span><span class="sxs-lookup"><span data-stu-id="f17c6-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="f17c6-182">如前所述，這些篩選條件定義所使用的自訂篩選條件只會將每個訊息所收到的其中一個篩選條件評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f17c6-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="f17c6-183">由於只有兩個篩選條件是使用這個篩選條件所定義，而且指定了同樣的群組設定，因此，結果會是路由服務在傳送至 regularCalcEndpoint 及 RoundingCalcEndpoint 之間交替。</span><span class="sxs-lookup"><span data-stu-id="f17c6-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4.  <span data-ttu-id="f17c6-184">若要針對篩選條件評估訊息，必須先將篩選資料表關聯至要用於接收訊息的服務端點。</span><span class="sxs-lookup"><span data-stu-id="f17c6-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="f17c6-185">下列範例示範如何使用路由行為將路由資料表關聯至服務端點：</span><span class="sxs-lookup"><span data-stu-id="f17c6-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="f17c6-186">範例</span><span class="sxs-lookup"><span data-stu-id="f17c6-186">Example</span></span>  
 <span data-ttu-id="f17c6-187">下列範例是完整的組態檔清單。</span><span class="sxs-lookup"><span data-stu-id="f17c6-187">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f17c6-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f17c6-188">See Also</span></span>  
 [<span data-ttu-id="f17c6-189">路由服務</span><span class="sxs-lookup"><span data-stu-id="f17c6-189">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
