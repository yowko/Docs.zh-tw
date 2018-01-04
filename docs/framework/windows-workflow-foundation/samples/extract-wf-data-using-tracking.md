---
title: "使用追蹤擷取 WF 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c269dc9c8b5a0050cfc3ffcefc3160b07c897
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="a3616-102">使用追蹤擷取 WF 資料</span><span class="sxs-lookup"><span data-stu-id="a3616-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="a3616-103">此範例會示範如何使用工作流程追蹤，從活動中擷取工作流程變數和引數。</span><span class="sxs-lookup"><span data-stu-id="a3616-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="a3616-104">也會示範如何加入追蹤記錄的註釋，以及在自訂追蹤記錄內擷取資料裝載。</span><span class="sxs-lookup"><span data-stu-id="a3616-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="a3616-105">此範例會使用 Windows 事件追蹤 (ETW) 追蹤參與者，從工作流程中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="a3616-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a3616-106">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="a3616-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="a3616-107"> 會提供可取得執行工作流程執行個體可見性的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a3616-107"> provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="a3616-108">追蹤執行階段會在工作流程執行期間發出工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="a3616-109">連同工作流程追蹤記錄，工作流程執行個體內的資料也可以從工作流程中擷取。</span><span class="sxs-lookup"><span data-stu-id="a3616-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="a3616-110">下列清單詳述可以從追蹤記錄中擷取的資料型別：</span><span class="sxs-lookup"><span data-stu-id="a3616-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="a3616-111">活動內的工作流程變數以及活動執行期間的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="a3616-112">為了擷取工作流程變數，要擷取的變數會指定在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="a3616-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="a3616-113">要擷取的變數只能使用 `ActivityStateQueries` 來指定。</span><span class="sxs-lookup"><span data-stu-id="a3616-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="a3616-114">下列程式碼範例會示範用來從活動中擷取工作流程變數的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="a3616-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  <span data-ttu-id="a3616-115">活動引數和活動狀態追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="a3616-116">引數會定義資料流入或流出活動的方式。</span><span class="sxs-lookup"><span data-stu-id="a3616-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="a3616-117">要擷取的引數會使用 <xref:System.Activities.Tracking.ActivityStateQuery> 來指定。下列程式碼範例是擷取 `Value` 引數的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="a3616-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  <span data-ttu-id="a3616-118">註釋是可以加入至發出之任何追蹤記錄的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="a3616-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="a3616-119">註釋會當做追蹤記錄的標記機制。</span><span class="sxs-lookup"><span data-stu-id="a3616-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="a3616-120">註釋會透過追蹤設定檔加入至追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="a3616-121">註釋可以加入至任何類型的工作流程追蹤查詢。</span><span class="sxs-lookup"><span data-stu-id="a3616-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="a3616-122">下列程式碼範例是一個追蹤設定檔，它會示範註釋如何加入至追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  <span data-ttu-id="a3616-123">自訂追蹤記錄是從使用者定義的活動所發出。</span><span class="sxs-lookup"><span data-stu-id="a3616-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="a3616-124">自訂追蹤記錄可以夾帶這個活動內定義的裝載資料。</span><span class="sxs-lookup"><span data-stu-id="a3616-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="a3616-125">訂閱追蹤設定檔內的自訂追蹤記錄可允許擷取追蹤記錄內的裝載。</span><span class="sxs-lookup"><span data-stu-id="a3616-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="a3616-126">自訂追蹤記錄可以使用自訂 <xref:System.Activities.Tracking.TrackingQuery> 來擷取。</span><span class="sxs-lookup"><span data-stu-id="a3616-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="a3616-127">下列程式碼範例是一個追蹤設定檔，它會擷取自訂追蹤記錄以及其裝載。</span><span class="sxs-lookup"><span data-stu-id="a3616-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="a3616-128">此範例示範如何擷取變數、引數和自訂記錄，以及使用 Web.config 中指定的設定檔來加入註釋。範例工作流程服務上會啟用追蹤，其方式是加入 `<etwTracking>` 行為項目。</span><span class="sxs-lookup"><span data-stu-id="a3616-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="a3616-129">下列程式碼範例會啟用 `ExtractWorkflowVariables` 追蹤設定檔的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a3616-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a3616-130">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="a3616-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="a3616-131">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WFStockPriceApplication.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="a3616-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a3616-132">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="a3616-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a3616-133">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="a3616-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="a3616-134">瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。</span><span class="sxs-lookup"><span data-stu-id="a3616-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="a3616-135">在瀏覽器中，按一下 StockPriceService.xamlx。</span><span class="sxs-lookup"><span data-stu-id="a3616-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="a3616-136">瀏覽器隨即顯示 StockPriceService 頁面，其中包含本機服務 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="a3616-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="a3616-137">複製此位址。</span><span class="sxs-lookup"><span data-stu-id="a3616-137">Copy this address.</span></span>  
  
     <span data-ttu-id="a3616-138">下列範例會顯示本機服務 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="a3616-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="a3616-139">叫用服務之前，啟動 [事件檢視器] 並確認事件記錄正在接聽從工作流程服務發出的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="a3616-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="a3616-140">從**啟動**功能表上，選取**系統管理工具**然後**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="a3616-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="a3616-141">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**，和**Microsoft**。</span><span class="sxs-lookup"><span data-stu-id="a3616-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="a3616-142">以滑鼠右鍵按一下**Microsoft**選取**檢視**然後**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="a3616-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="a3616-143">請確認**顯示分析與偵錯記錄檔**核取選項。</span><span class="sxs-lookup"><span data-stu-id="a3616-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="a3616-144">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a3616-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="a3616-145">以滑鼠右鍵按一下**分析**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="a3616-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="a3616-146">使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 開啟 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="a3616-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="a3616-147">WCF 測試用戶端 (WcfTestClient.exe) 位於\<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]安裝資料夾 > \Common7\IDE\ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3616-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="a3616-148">預設 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 安裝資料夾為 C:\Program Files\Microsoft Visual Studio 10.0。</span><span class="sxs-lookup"><span data-stu-id="a3616-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="a3616-149">在 WCF 測試用戶端中，選取**加入服務**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="a3616-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="a3616-150">新增您之前在輸入方塊中複製的本機服務 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="a3616-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="a3616-151">在 WCF 測試用戶端中，按兩下 `GetStockPrice`。</span><span class="sxs-lookup"><span data-stu-id="a3616-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="a3616-152">這樣會開啟 `GetStockPrice` 方法。</span><span class="sxs-lookup"><span data-stu-id="a3616-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="a3616-153">要求會接受一個參數。</span><span class="sxs-lookup"><span data-stu-id="a3616-153">The request accepts one parameter.</span></span> <span data-ttu-id="a3616-154">使用值**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="a3616-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="a3616-155">按一下**叫用**。</span><span class="sxs-lookup"><span data-stu-id="a3616-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="a3616-156">切換回 [事件檢視器] 並瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a3616-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="a3616-157">以滑鼠右鍵按一下**分析**選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="a3616-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="a3616-158">工作流程事件位於事件識別碼範圍 100-199。</span><span class="sxs-lookup"><span data-stu-id="a3616-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="a3616-159">事件包括可以在事件檢視器中檢視的註釋、變數、引數和自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="a3616-160">在事件檢視器中清除</span><span class="sxs-lookup"><span data-stu-id="a3616-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="a3616-161">您可以執行以下動作，在事件檢視器中清除事件記錄檔中的分析通道。</span><span class="sxs-lookup"><span data-stu-id="a3616-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="a3616-162">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="a3616-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="a3616-163">開啟 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="a3616-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="a3616-164">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a3616-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="a3616-165">以滑鼠右鍵按一下**分析**選取**停用記錄**。</span><span class="sxs-lookup"><span data-stu-id="a3616-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="a3616-166">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a3616-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="a3616-167">以滑鼠右鍵按一下**分析**選取**清除記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="a3616-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="a3616-168">選擇**清除**選項可清除事件。</span><span class="sxs-lookup"><span data-stu-id="a3616-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="a3616-169">已知問題</span><span class="sxs-lookup"><span data-stu-id="a3616-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3616-170">在 [事件檢視器] 中有一個可能無法為 ETW 事件解碼的已知問題。</span><span class="sxs-lookup"><span data-stu-id="a3616-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="a3616-171">您可能會看到類似下面的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a3616-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="a3616-172">如果您遇到這個錯誤，請按一下**重新整理**動作 窗格中。</span><span class="sxs-lookup"><span data-stu-id="a3616-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="a3616-173">現在，此事件應該就會正確解碼。</span><span class="sxs-lookup"><span data-stu-id="a3616-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a3616-174">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a3616-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a3616-175">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a3616-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a3616-176">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a3616-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3616-177">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a3616-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="a3616-178">請參閱</span><span class="sxs-lookup"><span data-stu-id="a3616-178">See Also</span></span>  
 [<span data-ttu-id="a3616-179">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="a3616-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
