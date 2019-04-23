---
title: 路由服務的 Hello World
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 37d2eaffa1ca5a4cce27c4950d00987828a61196
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329735"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="d5243-102">路由服務的 Hello World</span><span class="sxs-lookup"><span data-stu-id="d5243-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="d5243-103">這個範例會示範 Windows Communication Foundation (WCF) 路由服務。</span><span class="sxs-lookup"><span data-stu-id="d5243-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="d5243-104">路由服務是一種 WCF 元件，可讓您更輕鬆地在您的應用程式中加入內容為基礎的路由器。</span><span class="sxs-lookup"><span data-stu-id="d5243-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="d5243-105">此範例會調整標準 WCF 計算機範例，以便使用路由服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d5243-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="d5243-106">在此範例中，計算機用戶端設定為傳送訊息到路由器所公開的端點。</span><span class="sxs-lookup"><span data-stu-id="d5243-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="d5243-107">路由服務會設定為接受傳送給它的所有訊息，並將其轉送到對應於計算機服務的端點。</span><span class="sxs-lookup"><span data-stu-id="d5243-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="d5243-108">因此，傳送自用戶端的訊息會由路由器接收，然後再重新路由至實際的計算機服務。</span><span class="sxs-lookup"><span data-stu-id="d5243-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="d5243-109">來自計算機服務的訊息會傳送回路由器，接著再將其傳遞回計算機用戶端。</span><span class="sxs-lookup"><span data-stu-id="d5243-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="d5243-110">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="d5243-110">To use this sample</span></span>

1. <span data-ttu-id="d5243-111">使用 Visual Studio 2012，請開啟 HelloRoutingService.sln。</span><span class="sxs-lookup"><span data-stu-id="d5243-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="d5243-112">按下 F5 或 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="d5243-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d5243-113">如果按下 F5，計算機用戶端會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="d5243-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="d5243-114">如果您按下 CTRL+SHIFT+B (建置)，則必須自行啟動下列應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5243-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1.  <span data-ttu-id="d5243-115">計算機用戶端 (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="d5243-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2.  <span data-ttu-id="d5243-116">計算機服務 (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="d5243-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3.  <span data-ttu-id="d5243-117">路由服務 (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="d5243-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="d5243-118">按 ENTER 鍵以啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="d5243-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="d5243-119">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d5243-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="d5243-120">可透過程式碼或 App.Config 設定</span><span class="sxs-lookup"><span data-stu-id="d5243-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="d5243-121">此範例預設為使用 App.config 檔案定義路由器的行為。</span><span class="sxs-lookup"><span data-stu-id="d5243-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="d5243-122">您也可以將 App.config 檔案的名稱變更為其他任何名稱，讓其無法辨識，而且可以取消註解對 ConfigureRouterViaCode() 的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d5243-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="d5243-123">任一種方法都會在路由器中導致相同的行為。</span><span class="sxs-lookup"><span data-stu-id="d5243-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="d5243-124">情節</span><span class="sxs-lookup"><span data-stu-id="d5243-124">Scenario</span></span>
 <span data-ttu-id="d5243-125">此範例示範當做基本訊息幫浦的路由器。</span><span class="sxs-lookup"><span data-stu-id="d5243-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="d5243-126">路由服務會當做傳輸 Proxy 節點，而此節點設定為將訊息直接傳遞到一組預先設定的目的地端點。</span><span class="sxs-lookup"><span data-stu-id="d5243-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="d5243-127">真實情節</span><span class="sxs-lookup"><span data-stu-id="d5243-127">Real World Scenario</span></span>
 <span data-ttu-id="d5243-128">Contoso 希望增加它在命名、定址、設定及其服務安全性上所擁有的彈性。</span><span class="sxs-lookup"><span data-stu-id="d5243-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="d5243-129">若要這樣做，請將基本訊息幫浦放在其服務前方，以當做公開面對的端點。</span><span class="sxs-lookup"><span data-stu-id="d5243-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="d5243-130">這可讓它們在實際服務的前方增加額外的安全性，並使其在日後更容易實作向外延展的方案或服務版本控制。</span><span class="sxs-lookup"><span data-stu-id="d5243-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d5243-131">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d5243-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d5243-132">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d5243-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5243-133">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d5243-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5243-134">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d5243-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="d5243-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5243-135">See also</span></span>

- [<span data-ttu-id="d5243-136">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="d5243-136">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
