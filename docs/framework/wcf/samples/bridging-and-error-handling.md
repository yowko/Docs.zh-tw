---
title: "橋接及錯誤處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eec60855dc8ce3c611fa0fe3c8668973b43099b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="bridging-and-error-handling"></a><span data-ttu-id="7dfc9-102">橋接及錯誤處理</span><span class="sxs-lookup"><span data-stu-id="7dfc9-102">Bridging and Error Handling</span></span>
<span data-ttu-id="7dfc9-103">此範例示範如何將 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 路由服務用於使用不同繫結之用戶端和服務間的橋接通訊。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-103">This sample demonstrates how the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service is used for bridging communication between a client and a service that use different bindings.</span></span> <span data-ttu-id="7dfc9-104">此範例也會示範如何針對容錯移轉情況使用備份服務。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-104">This sample also shows how to use a back-up service for failover scenarios.</span></span> <span data-ttu-id="7dfc9-105">路由服務是一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件，該元件可讓它在應用程式中輕鬆加入內容架構的路由器。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-105">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="7dfc9-106">此範例會調整標準 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 計算機範例，以便使用路由服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-106">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the routing service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7dfc9-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7dfc9-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7dfc9-109">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7dfc9-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a><span data-ttu-id="7dfc9-111">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="7dfc9-111">Sample Details</span></span>  
 <span data-ttu-id="7dfc9-112">在此範例中，計算機用戶端設定為傳送訊息到路由器所公開的端點。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-112">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="7dfc9-113">路由服務會設定為接受傳送給它的所有訊息，並將其轉送到對應於計算機服務的端點。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-113">The routing service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="7dfc9-114">以下幾點描述主要計算機服務的組態、備份計算機服務與計算機用戶端，以及如何使用路由服務進行用戶端與服務之間的通訊：</span><span class="sxs-lookup"><span data-stu-id="7dfc9-114">The following points describe the configuration of the primary Calculator service, the back-up Calculator service, and the Calculator client and how the communication between the client and the service happens using the routing service:</span></span>  
  
-   <span data-ttu-id="7dfc9-115">計算機用戶端設定為使用 BasicHttpBinding，而計算機服務設定為使用 NetTcpBinding。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-115">The Calculator client is configured to use BasicHttpBinding while the Calculator service is configured to use NetTcpBinding.</span></span> <span data-ttu-id="7dfc9-116">路由服務會在必要時，先自動轉換訊息，然後再將其傳送至計算機服務，而且它也會轉換回應，讓計算機用戶端可以進行存取。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-116">The routing service automatically converts the messages as necessary before sending them to the Calculator service and it also converts the responses so that the Calculator client can access them.</span></span>  
  
-   <span data-ttu-id="7dfc9-117">路由服務知道兩個計算機服務：主要計算機服務和備份計算機服務。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-117">The routing service knows about two Calculator services: the primary Calculator service and the back-up Calculator service.</span></span> <span data-ttu-id="7dfc9-118">路由服務會先嘗試與主要計算機服務端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-118">The routing service first attempts to communicate with the primary Calculator service endpoint.</span></span> <span data-ttu-id="7dfc9-119">如果此嘗試因為端點中斷而失敗，則路由服務會嘗試與備份計算機服務端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-119">If this attempt fails due to the endpoint being down, the routing service then tries to communicate with the back-up Calculator service endpoint.</span></span>  
  
 <span data-ttu-id="7dfc9-120">因此，傳送自用戶端的訊息會由路由器接收，然後再重新路由至實際的計算機服務。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-120">Thus messages sent from the client are received by the router and are rerouted to the actual Calculator service.</span></span> <span data-ttu-id="7dfc9-121">如果計算機服務端點中斷，路由服務會將訊息路由至備份計算機服務端點。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-121">If the Calculator service endpoint is down, the routing service routes the message to the back-up Calculator service endpoint.</span></span> <span data-ttu-id="7dfc9-122">來自備份計算機服務的訊息會傳送回服務路由器，接著再將其傳遞回計算機用戶端。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-122">Messages from the back-up Calculator service are sent back to the service router, which in turn passes them back to the Calculator client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dfc9-123">備份清單可以定義多個端點。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-123">A back-up list can have more than one endpoint defined.</span></span> <span data-ttu-id="7dfc9-124">在此情況下，如果備份服務端點中斷，路由服務會嘗試連接到清單中的下一個備份端點，直到連線成功為止。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-124">In this case if the back-up service endpoint is down, the routing service attempts to connect to the next back-up endpoint in the list until a successful connection occurs.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7dfc9-125">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="7dfc9-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="7dfc9-126">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 RouterBridgingAndErrorHandling.sln。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-126">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open RouterBridgingAndErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="7dfc9-127">在 Visual Studio 中按下 F5 或 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-127">Press F5 or CTRL+SHIFT+B in Visual Studio</span></span>  
  
    1.  <span data-ttu-id="7dfc9-128">如果您想要按下 F5 時自動啟動必要的專案，以滑鼠右鍵按一下方案，請選取**屬性**，然後在**啟始專案**節點下的**的通用屬性**，選取**多個啟始專案**，並將所有專案都設定為**啟動**。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-128">If you would like to auto-launch the necessary projects when you press F5, right-click the solution, select **Properties**, and in the **Startup Project** node under **Common Properties**, select **Multiple Startup Projects**, and set all projects to **Start**.</span></span>  
  
    2.  <span data-ttu-id="7dfc9-129">如果您使用 CTRL+SHIFT+B 來建置專案，請啟動下列應用程式：</span><span class="sxs-lookup"><span data-stu-id="7dfc9-129">If you build the project with CTRL+SHIFT+B, start the following applications:</span></span>  
  
        1.  <span data-ttu-id="7dfc9-130">計算機用戶端 (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="7dfc9-130">Calculator client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="7dfc9-131">計算機服務 (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="7dfc9-131">Calculator service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="7dfc9-132">路由服務 (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="7dfc9-132">Routing Service (./RoutingService/bin/RoutingService.exe)</span></span>  
  
3.  <span data-ttu-id="7dfc9-133">在計算機用戶端中，按 ENTER 鍵以啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-133">In the Calculator Client, press ENTER to start the client.</span></span>  
  
     <span data-ttu-id="7dfc9-134">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7dfc9-134">You should see the following output:</span></span>  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="7dfc9-135">可透過程式碼或 App.config 設定</span><span class="sxs-lookup"><span data-stu-id="7dfc9-135">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="7dfc9-136">此範例預設為使用 App.config 檔案定義路由器的行為。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-136">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="7dfc9-137">您也可以將 App.config 檔案的名稱變更為其他任何名稱，讓其無法辨識，而且可以取消註解對 `ConfigureRouterViaCode()` 的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-137">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()`.</span></span> <span data-ttu-id="7dfc9-138">任一種方法都會在路由器中導致相同的行為。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-138">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="7dfc9-139">情節</span><span class="sxs-lookup"><span data-stu-id="7dfc9-139">Scenario</span></span>  
 <span data-ttu-id="7dfc9-140">此範例示範當做通訊協定橋接器與錯誤處理常式的服務路由器。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-140">This sample demonstrates the service router acting as a protocol bridge and error handler.</span></span> <span data-ttu-id="7dfc9-141">在此案例中，沒有發生內容架構的路由；路由服務會當做傳輸 Proxy 節點，而此節點設定為將訊息直接傳遞到一組預先設定的目的地端點。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-141">In this scenario, no content-based routing occurs; the routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span> <span data-ttu-id="7dfc9-142">路由服務也會執行嘗試傳送到設定為與其進行通訊之端點時所發生的其他透明處理錯誤步驟。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-142">The routing service also performs the additional steps of transparently handling errors that occur when it tries to send to the endpoints that it is configured to communicate with.</span></span> <span data-ttu-id="7dfc9-143">路由服務藉由當做路由橋接器使用，可讓使用者為外部通訊定義一個通訊協定，並為內部通訊定義另一個通訊協定。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-143">By acting as a protocol bridge, the routing service enables the user to define one protocol for external communication and another for internal communication.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="7dfc9-144">真實情節</span><span class="sxs-lookup"><span data-stu-id="7dfc9-144">Real World Scenario</span></span>  
 <span data-ttu-id="7dfc9-145">Contoso 想要在內部最佳化效能時，提供互通的服務端點給外界。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-145">Contoso wants to provide an interoperable service endpoint to the world, while optimizing performance internally.</span></span> <span data-ttu-id="7dfc9-146">因此，它會在內部使用路由服務將該連線橋接到使用其服務所使用之 NetTcpBinding 的端點時，透過端點使用 BasicHttpBinding，向外界公開其服務。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-146">Thus it exposes its services to the world through an endpoint using the BasicHttpBinding, while internally using the routing service to bridge that connection to the endpoint using NetTcpBinding, which its services use.</span></span> <span data-ttu-id="7dfc9-147">此外，Contoso 希望提供服務時能夠容許其中任何一個實際執行服務暫時中斷，然後使用錯誤處理功能視覺化路由器服務背後的多個端點，以便在需要時，自動容錯移轉到備份端點。</span><span class="sxs-lookup"><span data-stu-id="7dfc9-147">Furthermore, Contoso wants its service offering to be tolerant of temporary outages in any one of their production services and thus virtualizes multiple endpoints behind the router service using the ’s error handling capabilities to automatically failover to back-up endpoints when necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfc9-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfc9-148">See Also</span></span>  
 [<span data-ttu-id="7dfc9-149">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="7dfc9-149">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
