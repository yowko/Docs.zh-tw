---
title: WCF 服務及 Windows 的事件追蹤
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183204"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="4b383-102">WCF 服務及 Windows 的事件追蹤</span><span class="sxs-lookup"><span data-stu-id="4b383-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="4b383-103">此示例演示如何使用 Windows 通信基礎 （WCF） 中的分析跟蹤在 Windows 事件跟蹤 （ETW） 中發出事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="4b383-104">分析跟蹤是在 WCF 堆疊中的關鍵點發出的事件，允許在生產環境中對 WCF 服務進行故障排除。</span><span class="sxs-lookup"><span data-stu-id="4b383-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="4b383-105">WCF 服務中的分析跟蹤是可在生產環境中打開的跟蹤，對性能的影響最小。</span><span class="sxs-lookup"><span data-stu-id="4b383-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="4b383-106">這些追蹤都會做為事件發出至 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="4b383-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="4b383-107">此示例包括一個基本的 WCF 服務，其中事件從服務發送到事件日誌，可以使用事件檢視器查看。</span><span class="sxs-lookup"><span data-stu-id="4b383-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="4b383-108">還可以啟動專用 ETW 會話，該會話偵聽來自 WCF 服務的事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="4b383-109">這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。</span><span class="sxs-lookup"><span data-stu-id="4b383-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="4b383-110">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="4b383-110">To use this sample</span></span>

1. <span data-ttu-id="4b383-111">使用 Visual Studio 2012，打開 EtwAnalyticTraceSample.sln 解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="4b383-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="4b383-112">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="4b383-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="4b383-113">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="4b383-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="4b383-114">在 Web 瀏覽器中，按一下**計算機.svc**。</span><span class="sxs-lookup"><span data-stu-id="4b383-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="4b383-115">服務的 WSDL 文件 URI 應該會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="4b383-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="4b383-116">請複製該 URI。</span><span class="sxs-lookup"><span data-stu-id="4b383-116">Copy that URI.</span></span>

     <span data-ttu-id="4b383-117">預設情況下，服務開始偵聽埠 1378`http://localhost:1378/Calculator.svc`上的請求。</span><span class="sxs-lookup"><span data-stu-id="4b383-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="4b383-118">運行 WCF 測試用戶端 （WcfTestClient.exe）。</span><span class="sxs-lookup"><span data-stu-id="4b383-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="4b383-119">WCF 測試用戶端 （WcfTestClient.exe） 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。</span><span class="sxs-lookup"><span data-stu-id="4b383-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="4b383-120">預設的 Visual Studio 2012`C:\Program Files\Microsoft Visual Studio 10.0`安裝 dir 是 。</span><span class="sxs-lookup"><span data-stu-id="4b383-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="4b383-121">在 WCF 測試用戶端中，通過選擇**File**添加服務，然後**添加服務**。</span><span class="sxs-lookup"><span data-stu-id="4b383-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="4b383-122">在輸入方塊中加入端點位址。</span><span class="sxs-lookup"><span data-stu-id="4b383-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="4b383-123">預設值為 `http://localhost:1378/Calculator.svc`。</span><span class="sxs-lookup"><span data-stu-id="4b383-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="4b383-124">開啟 [事件檢視器] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b383-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="4b383-125">在調用服務之前，啟動事件檢視器並確保事件日誌偵聽從 WCF 服務發出的事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="4b383-126">在 **"開始"** 功能表中，選擇 **"管理工具**"，然後選擇**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="4b383-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="4b383-127">啟用**分析和\*\*\*\*調試**日誌。</span><span class="sxs-lookup"><span data-stu-id="4b383-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="4b383-128">在事件檢視器中的樹狀檢視中，導航到**事件檢視器**、**應用程式和服務日誌**、**微軟\*\*\*\*、Windows，** 然後是**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="4b383-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4b383-129">按右鍵**應用程式伺服器應用程式**，選擇 **"查看**"，然後**顯示分析和調試日誌**。</span><span class="sxs-lookup"><span data-stu-id="4b383-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="4b383-130">確保選中 **"顯示分析日誌"和"調試日誌"** 選項。</span><span class="sxs-lookup"><span data-stu-id="4b383-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="4b383-131">啟用**分析**日誌。</span><span class="sxs-lookup"><span data-stu-id="4b383-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="4b383-132">在事件檢視器中的樹狀檢視中，導航到**事件檢視器**、**應用程式和服務日誌**、**微軟\*\*\*\*、Windows，** 然後是**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="4b383-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4b383-133">按右鍵 **"分析"** 並選擇**啟用日誌**。</span><span class="sxs-lookup"><span data-stu-id="4b383-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="4b383-134">若要測試服務</span><span class="sxs-lookup"><span data-stu-id="4b383-134">To test the service</span></span>

1. <span data-ttu-id="4b383-135">切換回 WCF 測試用戶端並按兩下`Divide`並保留預設值，其中指定分母 0。</span><span class="sxs-lookup"><span data-stu-id="4b383-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="4b383-136">如果分母為 0，則服務會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b383-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="4b383-137">請查看服務所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="4b383-138">切換回事件檢視器，並導航到**事件檢視器**、**應用程式和服務日誌**、**微軟\*\*\*\*、Windows，** 然後是**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="4b383-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4b383-139">按右鍵 **"分析"** 並選擇 **"刷新**"。</span><span class="sxs-lookup"><span data-stu-id="4b383-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="4b383-140">WCF 分析追蹤事件會在事件檢視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="4b383-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="4b383-141">請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="4b383-142">重複步驟 1 和 2，但使用有效的輸入。</span><span class="sxs-lookup"><span data-stu-id="4b383-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="4b383-143">`N2` 參數的值可以是 0 以外的任何數字。</span><span class="sxs-lookup"><span data-stu-id="4b383-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="4b383-144">重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="4b383-145">此範例示範 WCF 服務所發出的分析追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="4b383-146">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="4b383-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="4b383-147">開啟 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="4b383-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="4b383-148">導航到**事件檢視器**、**應用程式和服務日誌**、**微軟\*\*\*\*、Windows，** 然後是**應用程式-伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="4b383-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="4b383-149">按右鍵 **"分析"** 並選擇 **"禁用日誌**"。</span><span class="sxs-lookup"><span data-stu-id="4b383-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="4b383-150">導航到**事件檢視器**、**應用程式和服務日誌**、**微軟\*\*\*\*、Windows，** 然後是**應用程式-伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="4b383-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="4b383-151">按右鍵 **"分析"** 並選擇 **"清除日誌**"。</span><span class="sxs-lookup"><span data-stu-id="4b383-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="4b383-152">選擇 **"清除"** 選項以清除事件。</span><span class="sxs-lookup"><span data-stu-id="4b383-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b383-153">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4b383-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4b383-154">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4b383-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4b383-155">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="4b383-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b383-156">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4b383-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="4b383-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b383-157">See also</span></span>

- <span data-ttu-id="4b383-158">[AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4b383-158">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
