---
title: 進階的錯誤處理
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084139"
---
# <a name="advanced-error-handling"></a><span data-ttu-id="2e528-102">進階的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="2e528-102">Advanced Error Handling</span></span>
<span data-ttu-id="2e528-103">這個範例會示範 Windows Communication Foundation (WCF) 路由服務。</span><span class="sxs-lookup"><span data-stu-id="2e528-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="2e528-104">路由服務是一種 WCF 元件，可讓您更輕鬆地在您的應用程式中加入內容為基礎的路由器。</span><span class="sxs-lookup"><span data-stu-id="2e528-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="2e528-105">此範例示範路由服務如何使用異動和其他更複雜的訊息處理概念，例如多點傳送，以聰明的方式從錯誤中復原。</span><span class="sxs-lookup"><span data-stu-id="2e528-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e528-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2e528-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e528-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2e528-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e528-108">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="2e528-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e528-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="2e528-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="2e528-110">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="2e528-110">Sample Details</span></span>  
 <span data-ttu-id="2e528-111">在此範例中，路由服務會設定為從 MSMQ 佇列讀取訊息，並且將此訊息多點傳送至兩個佇列清單。</span><span class="sxs-lookup"><span data-stu-id="2e528-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="2e528-112">其中一個清單用於服務佇列，另一個用於記錄佇列。</span><span class="sxs-lookup"><span data-stu-id="2e528-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="2e528-113">根據預設，由於設定路由服務使用的 MSMQ 繫結支援使用交易，因此路由服務會先確保訊息為交易式並且由每個清單的至少一個佇列接收，再向傳入佇列 (`InQ`) 回報訊息已成功路由傳送。</span><span class="sxs-lookup"><span data-stu-id="2e528-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="2e528-114">因此，在兩個服務佇列或兩個記錄佇列都無法使用的情況下，路由服務會回報訊息無法路由傳送，且傳入佇列應採取動作。</span><span class="sxs-lookup"><span data-stu-id="2e528-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="2e528-115">這個動作包括將訊息移至系統寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="2e528-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2e528-116">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="2e528-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="2e528-117">請先安裝 MSMQ，再執行此範例。</span><span class="sxs-lookup"><span data-stu-id="2e528-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="2e528-118">如果未安裝 MSMQ，則會在執行範例時傳回例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="2e528-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="2e528-119">可以找到安裝 MSMQ 的指示，在[安裝訊息佇列 (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437)。</span><span class="sxs-lookup"><span data-stu-id="2e528-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="2e528-120">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 AdvancedErrorHandling.sln。</span><span class="sxs-lookup"><span data-stu-id="2e528-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="2e528-121">按下**F5**或是**CTRL + SHIFT + B** Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="2e528-121">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="2e528-122">如果您使用 CTRL+SHIFT+B 來建置應用程式，就必須啟動位於 ./RoutingService/bin/debug/RoutingService.exe 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e528-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="2e528-123">在主控台視窗中按 ENTER 鍵，以啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="2e528-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="2e528-124">用戶端會分別為每個案例的佇列傳回不同的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2e528-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="2e528-125">以下是針對案例 1 傳回的輸出 (沒有錯誤)。</span><span class="sxs-lookup"><span data-stu-id="2e528-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="2e528-126">以下是針對案例 3 傳回的輸出 (主要服務和記錄佇列發生錯誤)。</span><span class="sxs-lookup"><span data-stu-id="2e528-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="2e528-127">以下是針對案例 4 傳回的輸出 (主要服務佇列及主要和備份記錄佇列發生錯誤)。</span><span class="sxs-lookup"><span data-stu-id="2e528-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="2e528-128">以下是針對案例 2 傳回的輸出 (主要服務佇列發生錯誤)。</span><span class="sxs-lookup"><span data-stu-id="2e528-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="2e528-129">可透過程式碼或 App.config 設定</span><span class="sxs-lookup"><span data-stu-id="2e528-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="2e528-130">此範例預設為使用 App.config 檔案定義路由器的行為。</span><span class="sxs-lookup"><span data-stu-id="2e528-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="2e528-131">您也可以將 RoutingService\App.config 檔案的名稱變更為其他名稱，使其無法辨識，並且將 RoutingService\Program.cs 中 `configDriven` 欄位的值變更為 `false`，以使用程式碼中定義的組態。</span><span class="sxs-lookup"><span data-stu-id="2e528-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="2e528-132">任一種方法都會在路由器中導致相同的行為。</span><span class="sxs-lookup"><span data-stu-id="2e528-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="2e528-133">情節</span><span class="sxs-lookup"><span data-stu-id="2e528-133">Scenario</span></span>  
 <span data-ttu-id="2e528-134">這個範例示範路由服務可以處理進階訊息處理功能，例如交易和接收內容，以及在正確處理錯誤案例中示範路由服務可以利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="2e528-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="2e528-135">真實情節</span><span class="sxs-lookup"><span data-stu-id="2e528-135">Real World Scenario</span></span>  
 <span data-ttu-id="2e528-136">Contoso 想要透過路由服務使用交易式接收，確保即使在錯誤情況下，所有必要的服務都能接收資訊。</span><span class="sxs-lookup"><span data-stu-id="2e528-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="2e528-137">除此之外，他們還希望能夠正確地自動處理錯誤，並且在使用錯誤處理邏輯時，於訊息無法傳遞的情況下回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e528-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="2e528-138">基於這個目的，他們設定讓路由服務依預期容錯移轉至特定端點，且路由服務會處理錯誤情況，包括在必要時建立、完成和復原/中止異動/接收內容。</span><span class="sxs-lookup"><span data-stu-id="2e528-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e528-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e528-139">See Also</span></span>  
 [<span data-ttu-id="2e528-140">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="2e528-140">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
