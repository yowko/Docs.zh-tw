---
title: 進階篩選
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805438"
---
# <a name="advanced-filters"></a><span data-ttu-id="6c07c-102">進階篩選</span><span class="sxs-lookup"><span data-stu-id="6c07c-102">Advanced Filters</span></span>
<span data-ttu-id="6c07c-103">這個範例會示範 Windows Communication Foundation (WCF) 的路由服務。</span><span class="sxs-lookup"><span data-stu-id="6c07c-103">This sample demonstrates a Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="6c07c-104">路由服務是一種 WCF 元件，可讓您更輕鬆地在您的應用程式中加入內容為基礎的路由器。</span><span class="sxs-lookup"><span data-stu-id="6c07c-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="6c07c-105">此範例會調整標準的 WCF 計算機範例，以便使用路由服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6c07c-105">This sample adapts the standard WCF Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="6c07c-106">此範例示範如何透過訊息篩選與訊息篩選資料表的使用，定義以內容為基礎的路由邏輯。</span><span class="sxs-lookup"><span data-stu-id="6c07c-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c07c-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6c07c-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6c07c-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6c07c-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c07c-109">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6c07c-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c07c-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6c07c-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="6c07c-111">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c07c-111">Sample Details</span></span>  
 <span data-ttu-id="6c07c-112">下表顯示加入至路由服務之訊息篩選資料表的訊息篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="6c07c-113">篩選器</span><span class="sxs-lookup"><span data-stu-id="6c07c-113">Filter</span></span>|<span data-ttu-id="6c07c-114">規則</span><span class="sxs-lookup"><span data-stu-id="6c07c-114">Rule</span></span>|<span data-ttu-id="6c07c-115">優先權</span><span class="sxs-lookup"><span data-stu-id="6c07c-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="6c07c-116">If (有標頭)</span><span class="sxs-lookup"><span data-stu-id="6c07c-116">If (has header)</span></span>|<span data-ttu-id="6c07c-117">四捨五入</span><span class="sxs-lookup"><span data-stu-id="6c07c-117">Rounding</span></span>|<span data-ttu-id="6c07c-118">2</span><span class="sxs-lookup"><span data-stu-id="6c07c-118">2</span></span>|  
|<span data-ttu-id="6c07c-119">If (顯示在 Ep2 上)</span><span class="sxs-lookup"><span data-stu-id="6c07c-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="6c07c-120">Regular</span><span class="sxs-lookup"><span data-stu-id="6c07c-120">Regular</span></span>|<span data-ttu-id="6c07c-121">1</span><span class="sxs-lookup"><span data-stu-id="6c07c-121">1</span></span>|  
|<span data-ttu-id="6c07c-122">If (與 Address2 一起顯示)</span><span class="sxs-lookup"><span data-stu-id="6c07c-122">If (showed up with Address2)</span></span>|<span data-ttu-id="6c07c-123">四捨五入</span><span class="sxs-lookup"><span data-stu-id="6c07c-123">Rounding</span></span>|<span data-ttu-id="6c07c-124">1</span><span class="sxs-lookup"><span data-stu-id="6c07c-124">1</span></span>|  
|<span data-ttu-id="6c07c-125">If (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="6c07c-125">If (RoundRobin1)</span></span>|<span data-ttu-id="6c07c-126">Regular</span><span class="sxs-lookup"><span data-stu-id="6c07c-126">Regular</span></span>|<span data-ttu-id="6c07c-127">0</span><span class="sxs-lookup"><span data-stu-id="6c07c-127">0</span></span>|  
|<span data-ttu-id="6c07c-128">If (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="6c07c-128">If (RoundRobin2)</span></span>|<span data-ttu-id="6c07c-129">四捨五入</span><span class="sxs-lookup"><span data-stu-id="6c07c-129">Rounding</span></span>|<span data-ttu-id="6c07c-130">0</span><span class="sxs-lookup"><span data-stu-id="6c07c-130">0</span></span>|  
  
 <span data-ttu-id="6c07c-131">您可以透過程式碼或在應用程式組態檔中建立與設定訊息篩選和訊息篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="6c07c-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="6c07c-132">針對這個範例，您可以尋找透過 RoutingService\routing.cs 檔中之程式碼定義的訊息篩選和訊息篩選資料表，或尋找在 RoutingService\App.config 檔中之應用程式組態檔定義的訊息篩選和訊息篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="6c07c-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="6c07c-133">以下段落描述如何透過程式碼建立此範例的訊息篩選和訊息篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="6c07c-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="6c07c-134">首先，<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 會尋找自訂標頭。</span><span class="sxs-lookup"><span data-stu-id="6c07c-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="6c07c-135">請注意，<xref:System.ServiceModel.WSHttpBinding> 會導致使用 SOAP 1.2 的封套版本，因此，XPath 陳述式會定義為使用 SOAP 1.2 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6c07c-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="6c07c-136"><xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 的預設命名空間管理員已經為 SOAP 1.2 命名空間定義一個可以使用的前置詞 /s12。</span><span class="sxs-lookup"><span data-stu-id="6c07c-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="6c07c-137">不過，預設命名空間管理員沒有用戶端用來定義實際標頭值的自訂命名空間，因此必須定義該前置詞。</span><span class="sxs-lookup"><span data-stu-id="6c07c-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="6c07c-138">與此標頭一起顯示的任何訊息都符合此篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="6c07c-139">第二個篩選是 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>，這個篩選會比對在 `calculatorEndpoint` 上收到的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="6c07c-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="6c07c-140">建立服務端點物件時，會定義端點名稱。</span><span class="sxs-lookup"><span data-stu-id="6c07c-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="6c07c-141">第三個篩選是 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="6c07c-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="6c07c-142">這會比對端點上顯示的任何訊息以及符合提供之位址前置詞 (或前方部分) 的位址。</span><span class="sxs-lookup"><span data-stu-id="6c07c-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="6c07c-143">在此範例中定義的位址前置詞為"http://localhost/routingservice/router/rounding/」。</span><span class="sxs-lookup"><span data-stu-id="6c07c-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="6c07c-144">這表示任何傳入的訊息傳送到 「 http://localhost/routingservice/router/rounding/\*"符合此篩選器。</span><span class="sxs-lookup"><span data-stu-id="6c07c-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/\*" are matched by this filter.</span></span> <span data-ttu-id="6c07c-145">在此情況下，它會顯示在 Rounding Calculator 端點的訊息具有位址"http://localhost/routingservice/router/rounding/calculator」。</span><span class="sxs-lookup"><span data-stu-id="6c07c-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="6c07c-146">最後兩個訊息篩選是自訂 <xref:System.ServiceModel.Dispatcher.MessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="6c07c-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="6c07c-147">在此範例中，會使用 "RoundRobin" 訊息篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="6c07c-148">此訊息篩選是在提供的 RoutingService\RoundRobinMessageFilter.cs 檔案中建立的。</span><span class="sxs-lookup"><span data-stu-id="6c07c-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="6c07c-149">設定為相同群組時，這些篩選會輪流報告它們是否符合訊息，因此，一次只有其中一個篩選會回應 `true`。</span><span class="sxs-lookup"><span data-stu-id="6c07c-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="6c07c-150">接著，所有這些訊息都會加入到 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>。</span><span class="sxs-lookup"><span data-stu-id="6c07c-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="6c07c-151">這樣做時，會指定優先權來影響訊息篩選資料表執行篩選的順序。</span><span class="sxs-lookup"><span data-stu-id="6c07c-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="6c07c-152">優先權越高，執行篩選的順序越前面；優先權越低，執行篩選的順序越後面。</span><span class="sxs-lookup"><span data-stu-id="6c07c-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="6c07c-153">因此，優先權為 2 的篩選會在優先權為 1 的篩選前面執行。</span><span class="sxs-lookup"><span data-stu-id="6c07c-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="6c07c-154">如果未指定優先權層級，則預設優先權層級為 0。</span><span class="sxs-lookup"><span data-stu-id="6c07c-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="6c07c-155">訊息篩選資料表會先在給定的優先權層級執行所有篩選，然後再移到次低的優先權層級。</span><span class="sxs-lookup"><span data-stu-id="6c07c-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="6c07c-156">如果在特定優先權找到相符項目，則訊息篩選資料表不會繼續嘗試在次低優先權尋找相符項目。</span><span class="sxs-lookup"><span data-stu-id="6c07c-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c07c-157">雖然此範例示範如何使用訊息篩選優先權，但一般而言，設計與設定您的篩選，讓它們不需要排定優先權便可正確運作是更具效能且更好的設計。</span><span class="sxs-lookup"><span data-stu-id="6c07c-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="6c07c-158">要加入的第一個篩選是 XPath 篩選，且其優先權設定為 2。</span><span class="sxs-lookup"><span data-stu-id="6c07c-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="6c07c-159">這是執行的第一個訊息篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-159">This is the first message filter that executes.</span></span> <span data-ttu-id="6c07c-160">如果此篩選找到自訂標頭，不論其他篩選的結果為何，都會將訊息路由至 Rounding Calculator 端點。</span><span class="sxs-lookup"><span data-stu-id="6c07c-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="6c07c-161">在優先權 1 會加入兩個篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="6c07c-162">同樣地，只有在優先權 2 的 XPath 篩選不符合訊息時，才會執行這些篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="6c07c-163">這兩個篩選會示範兩種不同的方式來判斷訊息顯示時的位址。</span><span class="sxs-lookup"><span data-stu-id="6c07c-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="6c07c-164">由於這兩個篩選會有效地檢查訊息是否到達兩個端點中的一個端點，因此它們可以在相同的優先權層級執行，因為它們不會同時傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="6c07c-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="6c07c-165">最後，在優先權 0 (最低的優先權) 會執行 RoundRobin 訊息篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="6c07c-166">這些篩選是使用相同的群組名稱設定，因此一次只會符合其中一個篩選。</span><span class="sxs-lookup"><span data-stu-id="6c07c-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="6c07c-167">具有自訂標頭的所有訊息都已經路由，而且所有訊息的位址都設定為特定虛擬化端點，因此，RoundRobin 訊息篩選所處理的訊息只有位址為沒有自訂標頭之預設路由器端點的訊息。</span><span class="sxs-lookup"><span data-stu-id="6c07c-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="6c07c-168">這些訊息會針對每個呼叫的訊息切換，因此，一半的作業會前往 Regular Calculator 端點，而另一半的作業則會前往 Rounding Calculator 端點。</span><span class="sxs-lookup"><span data-stu-id="6c07c-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6c07c-169">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="6c07c-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="6c07c-170">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 AdvancedFilters.sln。</span><span class="sxs-lookup"><span data-stu-id="6c07c-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="6c07c-171">若要開啟 [**方案總管**，選取**方案總管]** 從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="6c07c-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="6c07c-172">在 Visual Studio 中，按下 F5 或 CTRL + SHIFT + B。</span><span class="sxs-lookup"><span data-stu-id="6c07c-172">Press F5 or CTRL+SHIFT+B in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="6c07c-173">如果您想要按 F5 時自動啟動必要的專案，以滑鼠右鍵按一下方案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6c07c-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="6c07c-174">選取 **啟始專案**下方的節點**通用屬性**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="6c07c-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="6c07c-175">選取 **多個啟始專案**選項按鈕，並將所有要有的專案設定**開始**動作。</span><span class="sxs-lookup"><span data-stu-id="6c07c-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="6c07c-176">如果您使用 CTRL+SHIFT+B 來建置專案，就必須啟動下列應用程式：</span><span class="sxs-lookup"><span data-stu-id="6c07c-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="6c07c-177">計算機用戶端 (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="6c07c-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="6c07c-178">計算機服務 (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="6c07c-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="6c07c-179">路由計算機服務 (./RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="6c07c-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="6c07c-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="6c07c-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="6c07c-181">在計算機用戶端的主控台視窗中按 ENTER 鍵，以啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="6c07c-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="6c07c-182">用戶端會傳回一個可從中選擇的目的地端點清單。</span><span class="sxs-lookup"><span data-stu-id="6c07c-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="6c07c-183">輸入端點的對應字母來選擇目的地端點，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="6c07c-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="6c07c-184">接著，用戶端會詢問您是否要加入自訂標頭。</span><span class="sxs-lookup"><span data-stu-id="6c07c-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="6c07c-185">按 Y 表示 [是]；按 N 表示 [否]，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="6c07c-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="6c07c-186">根據您所做的選擇，您應該會看到不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="6c07c-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="6c07c-187">以下是將自訂標頭加入至訊息時所傳回的輸出。</span><span class="sxs-lookup"><span data-stu-id="6c07c-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="6c07c-188">以下是選擇沒有自訂標頭之 Rounding Calculator 端點時所傳回的輸出。</span><span class="sxs-lookup"><span data-stu-id="6c07c-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="6c07c-189">以下是選擇沒有自訂標頭之 Regular Calculator 端點時所傳回的輸出。</span><span class="sxs-lookup"><span data-stu-id="6c07c-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="6c07c-190">以下是選擇沒有自訂標頭之 Default Router 端點時所傳回的輸出。</span><span class="sxs-lookup"><span data-stu-id="6c07c-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="6c07c-191">計算機服務與四捨五入計算機服務也會列印出針對其個別主控台視窗叫用之作業的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6c07c-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="6c07c-192">在用戶端主控台視窗中，輸入`quit`按下 ENTER 以結束。</span><span class="sxs-lookup"><span data-stu-id="6c07c-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="6c07c-193">在服務主控台視窗中按 ENTER 鍵，以終止服務。</span><span class="sxs-lookup"><span data-stu-id="6c07c-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="6c07c-194">可透過程式碼或 App.config 設定</span><span class="sxs-lookup"><span data-stu-id="6c07c-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="6c07c-195">此範例預設為使用 App.config 檔案定義路由器的行為。</span><span class="sxs-lookup"><span data-stu-id="6c07c-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="6c07c-196">您也可以將 RoutingService\App.config 檔案的名稱變更為其他任何名稱，讓其無法辨識，而且可以在 RoutingService\routing.cs 中取消註解對 `ConfigureRouterViaCode()` 的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c07c-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="6c07c-197">任一種方法都會在路由器中導致相同的行為。</span><span class="sxs-lookup"><span data-stu-id="6c07c-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="6c07c-198">情節</span><span class="sxs-lookup"><span data-stu-id="6c07c-198">Scenario</span></span>  
 <span data-ttu-id="6c07c-199">此範例示範當做以內容為基礎之路由器運作的路由器，此路由器可透過一個端點公開服務的多個類型或實作。</span><span class="sxs-lookup"><span data-stu-id="6c07c-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="6c07c-200">真實情節</span><span class="sxs-lookup"><span data-stu-id="6c07c-200">Real World Scenario</span></span>  
 <span data-ttu-id="6c07c-201">Contoso 想要虛擬化其所有服務，僅公開一個端點，透過這個端點可以存取多個不同類型的服務。</span><span class="sxs-lookup"><span data-stu-id="6c07c-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="6c07c-202">在此情況下，它們會利用路由服務以內容為基礎的路由功能，決定應該將傳入要求傳送至何處。</span><span class="sxs-lookup"><span data-stu-id="6c07c-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c07c-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c07c-203">See Also</span></span>  
 [<span data-ttu-id="6c07c-204">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="6c07c-204">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
