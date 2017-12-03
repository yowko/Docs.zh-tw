---
title: "暫停的執行個體管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24c94f93524f6b31b622c527da068379ce7e724d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="suspended-instance-management"></a><span data-ttu-id="5369c-102">暫停的執行個體管理</span><span class="sxs-lookup"><span data-stu-id="5369c-102">Suspended Instance Management</span></span>
<span data-ttu-id="5369c-103">這個範例會示範如何管理已暫止的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="5369c-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="5369c-104"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 的預設動作為 `AbandonAndSuspend`。</span><span class="sxs-lookup"><span data-stu-id="5369c-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="5369c-105">這表示根據預設，從裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中之工作流程執行個體所擲回的未處理例外狀況將會造成此執行個體從記憶體中處置 (放棄)，而且此執行個體的永久性/持續版本將會標示為已暫停。</span><span class="sxs-lookup"><span data-stu-id="5369c-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="5369c-106">暫停的工作流程執行個體要等到取消暫停之後才能夠執行。</span><span class="sxs-lookup"><span data-stu-id="5369c-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>  
  
 <span data-ttu-id="5369c-107">此範例會示範如何實作命令列公用程式來查詢暫停的執行個體，以及如何提供使用者繼續或終止執行個體的選擇。</span><span class="sxs-lookup"><span data-stu-id="5369c-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="5369c-108">在這個範例中，工作流程服務會故意擲回例外狀況，使得它遭到暫停。</span><span class="sxs-lookup"><span data-stu-id="5369c-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="5369c-109">然後可以使用此命令列公用程式來查詢執行個體，之後再繼續或終止執行個體。</span><span class="sxs-lookup"><span data-stu-id="5369c-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5369c-110">示範</span><span class="sxs-lookup"><span data-stu-id="5369c-110">Demonstrates</span></span>  
 <span data-ttu-id="5369c-111">在 <xref:System.ServiceModel.WorkflowServiceHost> 中，<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 搭配 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 和 [!INCLUDE[wf](../../../../includes/wf-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5369c-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5369c-112">討論</span><span class="sxs-lookup"><span data-stu-id="5369c-112">Discussion</span></span>  
 <span data-ttu-id="5369c-113">這個範例中所實作的命令列公用程式是 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 隨附之 SQL 執行個體存放區實作所特有。</span><span class="sxs-lookup"><span data-stu-id="5369c-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="5369c-114">如果您擁有執行個體存放區的自訂實作，您可以改寫此公用程式，其方式是使用您的執行個體存放區所特有的實作來取代範例中的 `WorkflowInstanceCommand` 實作。</span><span class="sxs-lookup"><span data-stu-id="5369c-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>  
  
 <span data-ttu-id="5369c-115">提供的實作會直接針對 SQL 執行個體存放區來執行 SQL 命令，以列出暫停的執行個體，而且此實作會依賴加入至 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 的 <xref:System.ServiceModel.WorkflowServiceHost> 來結束或終止執行個體。</span><span class="sxs-lookup"><span data-stu-id="5369c-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5369c-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5369c-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5369c-117">本範例需要啟用下列 Windows 元件：</span><span class="sxs-lookup"><span data-stu-id="5369c-117">This sample requires that the following Windows components are enabled:</span></span>  
  
    1.  <span data-ttu-id="5369c-118">Microsoft Message Queues (MSMQ) 伺服器</span><span class="sxs-lookup"><span data-stu-id="5369c-118">Microsoft Message Queues (MSMQ) Server</span></span>  
  
    2.  <span data-ttu-id="5369c-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="5369c-119">SQL Server Express</span></span>  
  
2.  <span data-ttu-id="5369c-120">設定 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5369c-120">Set up the SQL Server database.</span></span>  
  
    1.  <span data-ttu-id="5369c-121">從[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]命令提示字元中執行"setup.cmd"，從 SuspendedInstanceManagement 範例目錄，會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5369c-121">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>  
  
        1.  <span data-ttu-id="5369c-122">使用 SQL Server Express 建立持續性資料庫。</span><span class="sxs-lookup"><span data-stu-id="5369c-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="5369c-123">如果持續性資料庫已經存在，請將它卸除然後重新建立。</span><span class="sxs-lookup"><span data-stu-id="5369c-123">If the persistence database already exists, then it is dropped and re-created</span></span>  
  
        2.  <span data-ttu-id="5369c-124">設定資料庫擁有持續性。</span><span class="sxs-lookup"><span data-stu-id="5369c-124">Sets up the database for persistence.</span></span>  
  
        3.  <span data-ttu-id="5369c-125">將 IIS APPPOOL\DefaultAppPool 和 NT AUTHORITY\Network Service 加入至 InstanceStoreUsers 角色，這是設定資料庫擁有持續性時所定義的角色。</span><span class="sxs-lookup"><span data-stu-id="5369c-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>  
  
3.  <span data-ttu-id="5369c-126">設定服務佇列。</span><span class="sxs-lookup"><span data-stu-id="5369c-126">Set up the service queue.</span></span>  
  
    1.  <span data-ttu-id="5369c-127">在[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，以滑鼠右鍵按一下**SampleWorkflowApp**專案，然後按一下**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="5369c-127">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>  
  
    2.  <span data-ttu-id="5369c-128">編譯及執行 SampleWorkflowApp 按**F5**。</span><span class="sxs-lookup"><span data-stu-id="5369c-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="5369c-129">這樣會建立所需的佇列。</span><span class="sxs-lookup"><span data-stu-id="5369c-129">This will create the required queue.</span></span>  
  
    3.  <span data-ttu-id="5369c-130">按**Enter**停止 SampleWorkflowApp。</span><span class="sxs-lookup"><span data-stu-id="5369c-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>  
  
    4.  <span data-ttu-id="5369c-131">從命令提示字元執行 Compmgmt.msc，開啟 [電腦管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="5369c-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>  
  
    5.  <span data-ttu-id="5369c-132">展開**服務和應用程式**，**訊息佇列**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="5369c-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    6.  <span data-ttu-id="5369c-133">以滑鼠右鍵按一下**ReceiveTx**佇列，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5369c-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>  
  
    7.  <span data-ttu-id="5369c-134">選取**安全性**索引標籤上，並允許**Everyone**擁有權限**接收訊息**，**查看訊息**，和**將訊息傳送**。</span><span class="sxs-lookup"><span data-stu-id="5369c-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>  
  
4.  <span data-ttu-id="5369c-135">現在，請執行範例。</span><span class="sxs-lookup"><span data-stu-id="5369c-135">Now, run the sample.</span></span>  
  
    1.  <span data-ttu-id="5369c-136">在[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，再次執行 SampleWorkflowApp 專案，但不偵錯按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5369c-136">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="5369c-137">兩個端點位址將會列印到主控台視窗：一個適用於應用程式端點，另一個來自 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="5369c-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="5369c-138">然後會建立工作流程執行個體，該執行個體的追蹤記錄將會出現在主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="5369c-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="5369c-139">工作流程執行個體將會擲回例外狀況，造成執行個體被暫停及中止。</span><span class="sxs-lookup"><span data-stu-id="5369c-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>  
  
    2.  <span data-ttu-id="5369c-140">然後可以使用此命令列公用程式來針對任何執行個體採取進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="5369c-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="5369c-141">命令列引數的語法如下：</span><span class="sxs-lookup"><span data-stu-id="5369c-141">The syntax for command line arguments is as follows::</span></span>  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         <span data-ttu-id="5369c-142">支援的命令為：`Query`、`Resume` 和 `Terminate`。</span><span class="sxs-lookup"><span data-stu-id="5369c-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="5369c-143">只有 `Resume` 和 `Terminate` 作業需要 InstanceId 參數。</span><span class="sxs-lookup"><span data-stu-id="5369c-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="5369c-144">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="5369c-144">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="5369c-145">從 `vs2010` 命令提示字元執行 Compmgmt.msc，開啟 [電腦管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="5369c-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>  
  
2.  <span data-ttu-id="5369c-146">展開**服務和應用程式**，**訊息佇列**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="5369c-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="5369c-147">刪除**ReceiveTx**佇列。</span><span class="sxs-lookup"><span data-stu-id="5369c-147">Delete the **ReceiveTx** queue.</span></span>  
  
4.  <span data-ttu-id="5369c-148">若要移除持續性資料庫，請執行 cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="5369c-148">To remove the persistence database, run cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5369c-149">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5369c-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5369c-150">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5369c-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5369c-151">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="5369c-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5369c-152">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5369c-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
