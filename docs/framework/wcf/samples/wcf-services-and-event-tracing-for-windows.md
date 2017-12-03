---
title: "WCF 服務及 Windows 的事件追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3b7b370ed6b1d9a900579ff0e6f1b0a22290c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="7db88-102">WCF 服務及 Windows 的事件追蹤</span><span class="sxs-lookup"><span data-stu-id="7db88-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="7db88-103">這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的分析追蹤功能發出 Windows 事件追蹤 (ETW) 中的事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="7db88-104">分析追蹤是在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 堆疊中的關鍵點發出，該堆疊允許在實際執行環境中進行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="7db88-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="7db88-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務中的分析追蹤是可以在實際執行環境中開啟的追蹤功能，對效能產生的影響相當小。</span><span class="sxs-lookup"><span data-stu-id="7db88-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="7db88-106">這些追蹤都會做為事件發出至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="7db88-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="7db88-107">這個範例包括基本的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，其中事件會從服務發出至事件記錄檔，而使用事件檢視器即可檢視此事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7db88-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="7db88-108">此外還可以啟動專用的 ETW 工作階段，以接聽來自 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="7db88-109">這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。</span><span class="sxs-lookup"><span data-stu-id="7db88-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7db88-110">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="7db88-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="7db88-111">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 EtwAnalyticTraceSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="7db88-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7db88-112">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="7db88-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7db88-113">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="7db88-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="7db88-114">在 Web 瀏覽器中，按一下**Calculator.svc**。</span><span class="sxs-lookup"><span data-stu-id="7db88-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="7db88-115">服務的 WSDL 文件 URI 應該會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="7db88-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="7db88-116">請複製該 URI。</span><span class="sxs-lookup"><span data-stu-id="7db88-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="7db88-117">根據預設，服務會開始接聽連接埠 1378 (http://localhost:1378/Calculator.svc) 上的要求。</span><span class="sxs-lookup"><span data-stu-id="7db88-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="7db88-118">執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端 (WcfTestClient.exe)。</span><span class="sxs-lookup"><span data-stu-id="7db88-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="7db88-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]測試用戶端 (WcfTestClient.exe) 位於\< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir> > \Common7\IDE\ WcfTestClient.exe (預設[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]安裝目錄是 C:\Program Files\Microsoft Visual Studio 10.0)。</span><span class="sxs-lookup"><span data-stu-id="7db88-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="7db88-120">內[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]測試用戶端中，選取 加入服務**檔案**，然後**加入服務**。</span><span class="sxs-lookup"><span data-stu-id="7db88-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="7db88-121">在輸入方塊中加入端點位址。</span><span class="sxs-lookup"><span data-stu-id="7db88-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="7db88-122">預設為 http://localhost:1378/Calculator.svc。</span><span class="sxs-lookup"><span data-stu-id="7db88-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="7db88-123">開啟 [事件檢視器] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7db88-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="7db88-124">叫用服務之前，啟動 [事件檢視器] 並確認事件記錄正在接聽從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務發出的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="7db88-125">從**啟動**功能表上，選取**系統管理工具**，然後**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="7db88-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="7db88-126">啟用**分析**和**偵錯**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7db88-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="7db88-127">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7db88-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="7db88-128">以滑鼠右鍵按一下**應用程式伺服器-應用程式**，選取**檢視**，然後**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="7db88-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="7db88-129">請確認**顯示分析與偵錯記錄檔**核取選項。</span><span class="sxs-lookup"><span data-stu-id="7db88-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="7db88-130">啟用**分析**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7db88-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="7db88-131">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7db88-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="7db88-132">以滑鼠右鍵按一下**分析**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="7db88-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="7db88-133">若要測試服務</span><span class="sxs-lookup"><span data-stu-id="7db88-133">To test the service</span></span>  
  
1.  <span data-ttu-id="7db88-134">切換回 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端，然後按兩下 `Divide` 並且保留預設值，這樣會將分母指定為 0。</span><span class="sxs-lookup"><span data-stu-id="7db88-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="7db88-135">如果分母為 0，則服務會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7db88-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="7db88-136">請查看服務所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="7db88-137">切換回 [事件檢視器] 並瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7db88-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="7db88-138">以滑鼠右鍵按一下**分析**選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="7db88-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="7db88-139">WCF 分析追蹤事件會在事件檢視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="7db88-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="7db88-140">請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="7db88-141">重複步驟 1 和 2，但使用有效的輸入。</span><span class="sxs-lookup"><span data-stu-id="7db88-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="7db88-142">`N2` 參數的值可以是 0 以外的任何數字。</span><span class="sxs-lookup"><span data-stu-id="7db88-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="7db88-143">重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="7db88-144">此範例示範 WCF 服務所發出的分析追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="7db88-145">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="7db88-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="7db88-146">開啟 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="7db88-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="7db88-147">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7db88-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="7db88-148">以滑鼠右鍵按一下**分析**選取**停用記錄**。</span><span class="sxs-lookup"><span data-stu-id="7db88-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="7db88-149">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7db88-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="7db88-150">以滑鼠右鍵按一下**分析**選取**清除記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="7db88-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="7db88-151">選擇**清除**選項可清除事件。</span><span class="sxs-lookup"><span data-stu-id="7db88-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7db88-152">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7db88-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7db88-153">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7db88-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7db88-154">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7db88-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7db88-155">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7db88-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="7db88-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7db88-156">See Also</span></span>  
 [<span data-ttu-id="7db88-157">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="7db88-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
