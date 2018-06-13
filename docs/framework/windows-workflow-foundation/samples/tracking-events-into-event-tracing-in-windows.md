---
title: 在 Windows 事件追蹤中追蹤事件
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 82de8ee74c12019f815adc63f2ca4441ad95d325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519502"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="e2dc2-102">在 Windows 事件追蹤中追蹤事件</span><span class="sxs-lookup"><span data-stu-id="e2dc2-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="e2dc2-103">這個範例示範如何啟用 Windows Workflow Foundation (WF) 追蹤工作流程服務上以及發出追蹤事件中事件的 Windows 追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="e2dc2-104">為了將工作流程追蹤記錄發出到 ETW，此範例會使用 ETW 追蹤參與者 (<xref:System.Activities.Tracking.EtwTrackingParticipant>)。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>  
  
 <span data-ttu-id="e2dc2-105">範例中的工作流程會接收要求、將對等的輸入資料指派給輸入變數，並將對等項目傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="e2dc2-106">當輸入資料為 0 時，將會發生除以零的例外狀況而無法處理，所以導致工作流程中止。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="e2dc2-107">當啟用追蹤時，錯誤追蹤記錄會發出到 ETW，有助於之後的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="e2dc2-108">ETW 追蹤參與者會設定追蹤設定檔來訂閱追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="e2dc2-109">追蹤設定檔會定義於 Web.config 檔案中，並當做組態參數提供給 ETW 追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="e2dc2-110">ETW 追蹤參與者會在工作流程服務的 Web.config 檔案中設定，而且會當做服務行為套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="e2dc2-111">在這個範例中，您會使用事件檢視器檢視事件記錄檔中的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>  
  
## <a name="workflow-tracking-details"></a><span data-ttu-id="e2dc2-112">工作流程追蹤詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2dc2-112">Workflow Tracking Details</span></span>  
 <span data-ttu-id="e2dc2-113">Windows Workflow Foundation 提供追蹤基礎結構，來追蹤工作流程執行個體執行。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="e2dc2-114">追蹤執行階段會建立工作流程執行個體，以發出與工作流程開發週期相關的事件、來自工作流程活動的事件和自訂事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="e2dc2-115">下表詳細說明追蹤基礎結構的主要元件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-115">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="e2dc2-116">元件</span><span class="sxs-lookup"><span data-stu-id="e2dc2-116">Component</span></span>|<span data-ttu-id="e2dc2-117">描述</span><span class="sxs-lookup"><span data-stu-id="e2dc2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2dc2-118">追蹤執行階段</span><span class="sxs-lookup"><span data-stu-id="e2dc2-118">Tracking runtime</span></span>|<span data-ttu-id="e2dc2-119">提供基礎結構以發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-119">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="e2dc2-120">追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="e2dc2-120">Tracking participants</span></span>|<span data-ttu-id="e2dc2-121">存取追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="e2dc2-122"> 隨附追蹤參與者，可將追蹤記錄當做 Windows 事件追蹤 (ETW) 事件撰寫。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-122"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="e2dc2-123">追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="e2dc2-123">Tracking profile</span></span>|<span data-ttu-id="e2dc2-124">篩選機制，可讓追蹤參與者訂閱從工作流程執行個體發出之追蹤記錄的子集。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="e2dc2-125">下表詳細說明工作流程執行階段發出的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-125">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="e2dc2-126">追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="e2dc2-126">Tracking record</span></span>|<span data-ttu-id="e2dc2-127">描述</span><span class="sxs-lookup"><span data-stu-id="e2dc2-127">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="e2dc2-128">工作流程執行個體追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="e2dc2-129">描述工作流程執行個體的開發週期。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="e2dc2-130">例如，當工作流程開始或完成時，就會發出執行個體記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="e2dc2-131">活動狀態追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-131">Activity state tracking records.</span></span>|<span data-ttu-id="e2dc2-132">活動執行詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-132">Details activity execution.</span></span> <span data-ttu-id="e2dc2-133">這些記錄會指出工作流程活動的狀態，例如活動排程時間、活動完成時間，或是擲回錯誤的時間。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="e2dc2-134">書籤繼續記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-134">Bookmark resumption record.</span></span>|<span data-ttu-id="e2dc2-135">只要工作流程執行個體中的書籤繼續，就會發出。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e2dc2-136">自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-136">Custom tracking records.</span></span>|<span data-ttu-id="e2dc2-137">工作流程作者可建立自訂追蹤記錄，並在自訂活動中發出這些記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="e2dc2-138">當活動排程另一個活動時，就會發出這個記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-138">This record is emitted when an activity schedules another activity.</span></span>|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="e2dc2-139">從活動中傳播錯誤時，就會發出這個記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-139">This record is emitted when a fault is propagated from an activity.</span></span>|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="e2dc2-140">當另一個活動取消原本的活動時，就會發出這個記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-140">This record is emitted when an activity is canceled by another activity.</span></span>|  
  
 <span data-ttu-id="e2dc2-141">追蹤參與者可使用追蹤設定檔訂閱所發出之追蹤記錄的子集。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="e2dc2-142">追蹤設定檔包含追蹤查詢，這些查詢允許訂閱特殊追蹤記錄類型。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="e2dc2-143">追蹤設定檔可在程式碼或組態中指定。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-143">Tracking profiles can be specified in code or in configuration.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e2dc2-144">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="e2dc2-144">To use this sample</span></span>  
  
1.  <span data-ttu-id="e2dc2-145">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 EtwTrackingParticipantSample.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-145">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EtwTrackingParticipantSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e2dc2-146">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-146">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e2dc2-147">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-147">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="e2dc2-148">根據預設，服務會接聽連接埠 53797 (http://localhost:53797/SampleWorkflowService.xamlx)。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>  
  
4.  <span data-ttu-id="e2dc2-149">使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 開啟 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-149">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="e2dc2-150">WCF 測試用戶端 (WcfTestClient.exe) 位於\<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]安裝資料夾 > \Common7\IDE\ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-150">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="e2dc2-151">預設 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 安裝資料夾為 C:\Program Files\Microsoft Visual Studio 10.0。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-151">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
5.  <span data-ttu-id="e2dc2-152">在 WCF 測試用戶端中，選取**加入服務**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="e2dc2-153">在輸入方塊中加入端點位址。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="e2dc2-154">預設值為 http://localhost:53797/SampleWorkflowService.xamlx。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-154">The default is http://localhost:53797/SampleWorkflowService.xamlx.</span></span>  
  
6.  <span data-ttu-id="e2dc2-155">開啟 [事件檢視器] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-155">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="e2dc2-156">在之前叫用服務，啟動 事件檢視器，從**啟動**功能表上，選取**執行**，並在輸入`eventvwr.exe`。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="e2dc2-157">確認事件記錄檔正在接聽從工作流程服務發出的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="e2dc2-158">在 事件檢視器的樹狀檢視中，瀏覽至**事件檢視器**， **Applications and Services Logs**，和**Microsoft**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="e2dc2-159">以滑鼠右鍵按一下**Microsoft**選取**檢視**然後**顯示分析與偵錯記錄檔**啟用分析與偵錯記錄檔</span><span class="sxs-lookup"><span data-stu-id="e2dc2-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>  
  
     <span data-ttu-id="e2dc2-160">請確認**顯示分析與偵錯記錄檔**核取選項。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
8.  <span data-ttu-id="e2dc2-161">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e2dc2-162">以滑鼠右鍵按一下**分析**選取**啟用記錄**啟用**分析**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>  
  
9. <span data-ttu-id="e2dc2-163">若要使用 WCF 測試用戶端測試此服務，請按兩下 `GetData`。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>  
  
     <span data-ttu-id="e2dc2-164">這樣會開啟 `GetData` 方法。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-164">This opens the `GetData` method.</span></span> <span data-ttu-id="e2dc2-165">此要求會接受一個參數，並確定值為 0 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>  
  
     <span data-ttu-id="e2dc2-166">按一下**叫用**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-166">Click **Invoke**.</span></span>  
  
10. <span data-ttu-id="e2dc2-167">請查看工作流程所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-167">Observe the events emitted from the workflow.</span></span>  
  
     <span data-ttu-id="e2dc2-168">切換回 [事件檢視器] 並瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e2dc2-169">以滑鼠右鍵按一下**分析**選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-169">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="e2dc2-170">工作流程事件會顯示在事件檢視器中。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="e2dc2-171">請注意，將會顯示工作流程執行事件，而且其中一個是未處理的例外狀況且對應到工作流程中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="e2dc2-172">此外，也會從工作流程活動發出警告事件，指出活動正在擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>  
  
11. <span data-ttu-id="e2dc2-173">使用 0 以外的輸入資料重複步驟 9 和 10，如此一來就不會擲回任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>  
  
 <span data-ttu-id="e2dc2-174">追蹤設定檔可讓您訂閱執行階段在工作流程執行個體狀態變更時，所發出的事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="e2dc2-175">根據您的監控需求，您可以建立初略的設定檔，使其訂閱工作流程上的一組小型高階狀態變更。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="e2dc2-176">在另一方面，您也可以建立非常精確的設定檔，它的輸出非常豐富，足以讓您在日後重新建構執行。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="e2dc2-177">此範例示範使用 `HealthMonitoring Tracking Profile` 從工作流程執行階段發出的事件，它會發出一組小型事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="e2dc2-178">發出其他工作流程追蹤事件的另一個設定檔名為 `Troubleshooting Tracking Profile`，它也會在 Web.config 中提供。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="e2dc2-179">當安裝 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 時，Machine.config 檔案中會設定有空白名稱的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="e2dc2-180">當沒有設定檔名稱或者指定了空的設定檔名稱時，這個設定檔會由 ETW 追蹤行為組態所使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>  
  
 <span data-ttu-id="e2dc2-181">狀況監控追蹤設定檔會發出工作流程執行個體記錄及活動錯誤傳播記錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="e2dc2-182">這個設定檔的建立方式，是將下列追蹤設定檔加入至 Web.config 組態檔。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="e2dc2-183">您可以將 `EtwTrackingParticipant` 組態變更為以下內容來變更此設定檔。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="e2dc2-184">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="e2dc2-184">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="e2dc2-185">開啟 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-185">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="e2dc2-186">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e2dc2-187">以滑鼠右鍵按一下**分析**選取**停用記錄**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-187">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="e2dc2-188">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e2dc2-189">以滑鼠右鍵按一下**分析**選取**清除記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-189">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="e2dc2-190">選擇**清除**選項可清除事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-190">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="e2dc2-191">已知問題</span><span class="sxs-lookup"><span data-stu-id="e2dc2-191">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2dc2-192">在 [事件檢視器] 中有一個可能無法為 ETW 事件解碼的已知問題。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="e2dc2-193">您可能會看到類似下面的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-193">You may see an error message that looks like the following.</span></span>  
>   
>  <span data-ttu-id="e2dc2-194">事件識別碼的描述\<識別碼 > 找不到 Microsoft Windows 應用程式伺服器-應用程式的來源。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="e2dc2-195">本機電腦可能並未安裝引發此事件的元件，或安裝已損毀。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="e2dc2-196">您可以在本機電腦上安裝或修復該元件。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-196">You can install or repair the component on the local computer.</span></span>  
>   
>  <span data-ttu-id="e2dc2-197">如果您遇到這個錯誤，請按一下執行窗格中的 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="e2dc2-198">現在，此事件應該就會正確解碼。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-198">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2dc2-199">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e2dc2-200">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2dc2-201">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2dc2-202">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e2dc2-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="e2dc2-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2dc2-203">See Also</span></span>  
 [<span data-ttu-id="e2dc2-204">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="e2dc2-204">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
