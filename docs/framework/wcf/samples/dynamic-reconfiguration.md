---
title: 動態重新組態
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 36b548ee47ed9165743bbfb1eaab5cf3bbe82bd2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="913e3-102">動態重新組態</span><span class="sxs-lookup"><span data-stu-id="913e3-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="913e3-103">此範例示範 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 路由服務。</span><span class="sxs-lookup"><span data-stu-id="913e3-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="913e3-104">路由服務是一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件，該元件可讓它在應用程式中輕鬆加入內容架構的路由器。</span><span class="sxs-lookup"><span data-stu-id="913e3-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="913e3-105">此範例會調整標準 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 計算機範例，以便使用路由服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="913e3-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="913e3-106">此範例示範如何在執行階段以動態方式重新設定路由服務。</span><span class="sxs-lookup"><span data-stu-id="913e3-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="913e3-107">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="913e3-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="913e3-108">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="913e3-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="913e3-109">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="913e3-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="913e3-110">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="913e3-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="913e3-111">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="913e3-111">Sample Details</span></span>  
 <span data-ttu-id="913e3-112">為了在執行階段期間以動態方式重新設定路由服務，此範例會每五秒引發一個建立新 <xref:System.ServiceModel.Routing.RoutingConfiguration> 物件的計時器並進行套用。</span><span class="sxs-lookup"><span data-stu-id="913e3-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="913e3-113">這個組態會參考 Regular Calculator 端點或 Rounding Calculator 端點。</span><span class="sxs-lookup"><span data-stu-id="913e3-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="913e3-114">計算機用戶端應用程式會根據當時路由服務設定為路由到哪個服務而定，從該服務傳回其訊息。</span><span class="sxs-lookup"><span data-stu-id="913e3-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="913e3-115">系統會使用路由服務透過自訂行為以動態方式重新設定的功能。</span><span class="sxs-lookup"><span data-stu-id="913e3-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="913e3-116">這個自訂行為會附加一個服務延伸，其中包含每五秒引發的簡易執行緒計時器，這個計時器會導致回呼 `UpdateRules` 方法。</span><span class="sxs-lookup"><span data-stu-id="913e3-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="913e3-117">此回呼會建立並套用新的路由組態。</span><span class="sxs-lookup"><span data-stu-id="913e3-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="913e3-118">在實際部署中，這個回呼可能會當做其他某些類型事件的結果達成，例如 SQL-Event 通知或 WS-Discovery 公告。</span><span class="sxs-lookup"><span data-stu-id="913e3-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="913e3-119">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="913e3-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="913e3-120">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 DynamicReconfiguration.sln。</span><span class="sxs-lookup"><span data-stu-id="913e3-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="913e3-121">若要開啟**方案總管 中**，選取**方案總管 中**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="913e3-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="913e3-122">按**F5**或**CTRL + SHIFT + B** Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="913e3-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="913e3-123">如果您想要自動啟動必要的專案時按下**F5**，以滑鼠右鍵按一下方案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="913e3-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="913e3-124">選取**啟始專案**節點下的**通用屬性**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="913e3-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="913e3-125">選取**多個啟始專案**選項按鈕，並將所有的專案設定**啟動**動作。</span><span class="sxs-lookup"><span data-stu-id="913e3-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="913e3-126">如果您使用建置專案**CTRL + SHIFT + B**，您必須啟動下列應用程式：</span><span class="sxs-lookup"><span data-stu-id="913e3-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="913e3-127">計算機用戶端 (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="913e3-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="913e3-128">計算機服務 (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="913e3-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="913e3-129">路由計算機服務 (./RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="913e3-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="913e3-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="913e3-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="913e3-131">在計算機用戶端的主控台視窗中，按下 ENTER 啟動用戶端並呼叫計算機服務作業。</span><span class="sxs-lookup"><span data-stu-id="913e3-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="913e3-132">路由服務會將訊息輪流路由至 Rounding Calculator 和 Regular Calculator，因為路由組態每五秒便會動態變更一次。</span><span class="sxs-lookup"><span data-stu-id="913e3-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="913e3-133">根據路由服務設定將訊息傳送到哪個端點而定，在用戶端主控台視窗中會有不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="913e3-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="913e3-134">重複持續按下 ENTER 超過五秒，然後從服務的結果中觀察變更。</span><span class="sxs-lookup"><span data-stu-id="913e3-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="913e3-135">以下是路由器服務設定為將訊息路由至 Rounding Calculator 服務時所傳回的輸出。</span><span class="sxs-lookup"><span data-stu-id="913e3-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="913e3-136">以下是路由服務設定為將訊息路由至 Regular Calculator 服務時所傳回的輸出。</span><span class="sxs-lookup"><span data-stu-id="913e3-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="913e3-137">計算機服務與四捨五入計算機服務也會列印出針對其個別主控台視窗叫用之作業的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="913e3-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="913e3-138">在用戶端主控台視窗中，輸入"quit"，然後按 ENTER 以結束。</span><span class="sxs-lookup"><span data-stu-id="913e3-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="913e3-139">在服務主控台視窗中按 ENTER 鍵，以終止服務。</span><span class="sxs-lookup"><span data-stu-id="913e3-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="913e3-140">情節</span><span class="sxs-lookup"><span data-stu-id="913e3-140">Scenario</span></span>  
 <span data-ttu-id="913e3-141">此範例示範當做以內容為基礎之路由器運作的路由器，此路由器可透過一個端點公開服務的多個類型或實作。</span><span class="sxs-lookup"><span data-stu-id="913e3-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="913e3-142">真實情節</span><span class="sxs-lookup"><span data-stu-id="913e3-142">Real World Scenario</span></span>  
 <span data-ttu-id="913e3-143">Contoso 想要虛擬化其所有服務，僅公開一個端點，透過這個端點可以存取多個不同類型的服務。</span><span class="sxs-lookup"><span data-stu-id="913e3-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="913e3-144">在此情況下，它們會利用路由服務以內容為基礎的路由功能，決定應該將傳入要求傳送至何處。</span><span class="sxs-lookup"><span data-stu-id="913e3-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913e3-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="913e3-145">See Also</span></span>  
 [<span data-ttu-id="913e3-146">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="913e3-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
