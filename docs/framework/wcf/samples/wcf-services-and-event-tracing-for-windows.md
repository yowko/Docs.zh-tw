---
title: WCF 服務及 Windows 的事件追蹤
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 35d0202a3b9cf4060240dc521554644d419a5c23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338965"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="ee195-102">WCF 服務及 Windows 的事件追蹤</span><span class="sxs-lookup"><span data-stu-id="ee195-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="ee195-103">此範例示範如何使用 Windows Communication Foundation (WCF) 中的分析追蹤功能發出的事件追蹤的 Windows (ETW) 事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="ee195-104">分析追蹤是在 WCF 堆疊中的 WCF 服務，在生產環境中疑難排解的關鍵點發出的事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="ee195-105">WCF 服務中的分析追蹤追蹤，可以開啟在生產環境中對效能的影響降到最低。</span><span class="sxs-lookup"><span data-stu-id="ee195-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="ee195-106">這些追蹤都會做為事件發出至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="ee195-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="ee195-107">此範例包含基本的 WCF 服務，在其中事件會從服務發出至事件日誌中，您可以使用事件檢視器檢視。</span><span class="sxs-lookup"><span data-stu-id="ee195-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="ee195-108">它也可啟動專用的 ETW 工作階段，它會接聽來自 WCF 服務的事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="ee195-109">這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。</span><span class="sxs-lookup"><span data-stu-id="ee195-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="ee195-110">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="ee195-110">To use this sample</span></span>

1. <span data-ttu-id="ee195-111">使用 Visual Studio 2012，請開啟 EtwAnalyticTraceSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="ee195-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="ee195-112">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="ee195-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="ee195-113">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="ee195-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="ee195-114">在網頁瀏覽器中，按一下**Calculator.svc**。</span><span class="sxs-lookup"><span data-stu-id="ee195-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="ee195-115">服務的 WSDL 文件 URI 應該會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="ee195-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="ee195-116">請複製該 URI。</span><span class="sxs-lookup"><span data-stu-id="ee195-116">Copy that URI.</span></span>

     <span data-ttu-id="ee195-117">根據預設，服務會開始接聽要求連接埠 1378年`http://localhost:1378/Calculator.svc`。</span><span class="sxs-lookup"><span data-stu-id="ee195-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="ee195-118">執行 WCF 測試用戶端 (WcfTestClient.exe)。</span><span class="sxs-lookup"><span data-stu-id="ee195-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="ee195-119">WCF 測試用戶端 (WcfTestClient.exe) 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。</span><span class="sxs-lookup"><span data-stu-id="ee195-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="ee195-120">預設 Visual Studio 2012 的安裝目錄是`C:\Program Files\Microsoft Visual Studio 10.0`。</span><span class="sxs-lookup"><span data-stu-id="ee195-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="ee195-121">在 WCF 測試用戶端，將服務新增所選取**檔案**，然後**加入服務**。</span><span class="sxs-lookup"><span data-stu-id="ee195-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="ee195-122">在輸入方塊中加入端點位址。</span><span class="sxs-lookup"><span data-stu-id="ee195-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="ee195-123">預設為 `http://localhost:1378/Calculator.svc`。</span><span class="sxs-lookup"><span data-stu-id="ee195-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="ee195-124">開啟 [事件檢視器] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee195-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="ee195-125">之前叫用服務，啟動 [事件檢視器] 並確認事件記錄檔正在接聽從 WCF 服務所發出的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="ee195-126">從**開始**功能表上，選取**系統管理工具**，然後**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="ee195-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="ee195-127">啟用**分析**並**偵錯**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ee195-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="ee195-128">在樹狀檢視中 事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ee195-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="ee195-129">以滑鼠右鍵按一下**應用程式伺服器-應用程式**，選取**檢視**，然後**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="ee195-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="ee195-130">請確認**顯示分析與偵錯記錄檔**核取選項。</span><span class="sxs-lookup"><span data-stu-id="ee195-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="ee195-131">啟用**分析**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ee195-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="ee195-132">在樹狀檢視中 事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ee195-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="ee195-133">以滑鼠右鍵按一下**分析**，然後選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="ee195-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="ee195-134">若要測試服務</span><span class="sxs-lookup"><span data-stu-id="ee195-134">To test the service</span></span>

1. <span data-ttu-id="ee195-135">切換回 WCF 測試用戶端，然後按兩下`Divide`並保留預設值，其中將分母指定為 0。</span><span class="sxs-lookup"><span data-stu-id="ee195-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="ee195-136">如果分母為 0，則服務會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee195-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="ee195-137">請查看服務所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="ee195-138">切換回 [事件檢視器] 並瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ee195-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="ee195-139">以滑鼠右鍵按一下**分析**，然後選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="ee195-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="ee195-140">WCF 分析追蹤事件會在事件檢視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="ee195-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="ee195-141">請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="ee195-142">重複步驟 1 和 2，但使用有效的輸入。</span><span class="sxs-lookup"><span data-stu-id="ee195-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="ee195-143">`N2` 參數的值可以是 0 以外的任何數字。</span><span class="sxs-lookup"><span data-stu-id="ee195-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="ee195-144">重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="ee195-145">此範例示範 WCF 服務所發出的分析追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="ee195-146">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="ee195-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="ee195-147">開啟 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="ee195-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="ee195-148">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ee195-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="ee195-149">以滑鼠右鍵按一下**分析**，然後選取**停用記錄**。</span><span class="sxs-lookup"><span data-stu-id="ee195-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="ee195-150">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ee195-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="ee195-151">以滑鼠右鍵按一下**分析**，然後選取**清除記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="ee195-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="ee195-152">選擇**清除**選項來清除事件。</span><span class="sxs-lookup"><span data-stu-id="ee195-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ee195-153">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ee195-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ee195-154">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ee195-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee195-155">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ee195-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee195-156">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ee195-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="ee195-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee195-157">See also</span></span>

- [<span data-ttu-id="ee195-158">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="ee195-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
