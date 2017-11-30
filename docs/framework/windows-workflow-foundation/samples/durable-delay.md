---
title: "永久性延遲"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7023d7548db99d511ae18ad4d52b9a8168c4243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="durable-delay"></a><span data-ttu-id="f2e5c-102">永久性延遲</span><span class="sxs-lookup"><span data-stu-id="f2e5c-102">Durable Delay</span></span>
<span data-ttu-id="f2e5c-103">這個範例示範如何使用永久性延遲，此延遲會在延遲期間將工作流程保存至永久性裝置。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="f2e5c-104">範例工作流程包含兩個主控台訊息，兩者之間會以延遲區隔。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="f2e5c-105">當延遲觸發時，工作流程便會卸載，並且在工作流程執行個體存放區中等待 5 秒鐘，再重新載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="f2e5c-106">工作流程詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2e5c-106">Workflow Details</span></span>  
 <span data-ttu-id="f2e5c-107">工作流程服務主機會透過載入和卸載的方式裝載工作流程，並且管理工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="f2e5c-108">為了啟動工作流程定義的執行個體，範例會設定一個 Proxy，以便將訊息傳送至工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="f2e5c-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> 屬性會設為 `true`，以便在收到訊息時，建立新的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="f2e5c-110">下列清單詳細描述工作流程服務主機在初始化期間的設定內容。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="f2e5c-111">建立具有位址的服務主機 (http://localhost:8080/Client)。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="f2e5c-112">在服務主機中建立端點，以便在工作流程內與 <xref:System.ServiceModel.Activities.Receive> 活動進行通訊。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="f2e5c-113">設定 SQL 執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="f2e5c-114">加入卸載執行個體的行為，該行為會指定工作流程服務主機應將工作流程執行個體卸載至 SQL 持續性存放區的情況。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="f2e5c-115">在這個範例中，它會在工作流程閒置後 (觸發延遲時) 立即卸載執行個體。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="f2e5c-116">建立 Proxy，將訊息傳送至工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f2e5c-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="f2e5c-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="f2e5c-118">設定持續性資料庫。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="f2e5c-119">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="f2e5c-120">瀏覽至[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]目錄 (C:\Windows\Microsoft.NET\Framework\v4。X\\)。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="f2e5c-121">編輯 WorkflowManagementService.exe.config 檔案，並將下列連接字串加入至 <`database`> 項目內。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="f2e5c-122">巡覽至 DurableDelay\CS 目錄。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="f2e5c-123">執行 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="f2e5c-124">執行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]使用提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="f2e5c-125">開啟 [Delay.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="f2e5c-126">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="f2e5c-127">按 CTRL+F5 執行方案。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="f2e5c-128">若要解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="f2e5c-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="f2e5c-129">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="f2e5c-130">巡覽至 DurableDelay\CS 目錄。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="f2e5c-131">執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2e5c-132">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2e5c-133">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f2e5c-134">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2e5c-135">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f2e5c-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`  
  
## <a name="see-also"></a><span data-ttu-id="f2e5c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2e5c-136">See Also</span></span>
