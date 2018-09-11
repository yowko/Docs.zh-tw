---
title: SQLStoreExtensibility
ms.date: 03/30/2017
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
ms.openlocfilehash: f49d05244cf9f65a8e06f39c7e40391aaebd9f77
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271136"
---
# <a name="sqlstoreextensibility"></a><span data-ttu-id="a860f-102">SQLStoreExtensibility</span><span class="sxs-lookup"><span data-stu-id="a860f-102">SQLStoreExtensibility</span></span>
<span data-ttu-id="a860f-103">這個範例示範 SQL 工作流程執行個體存放區中已提升屬性的使用方式和組態。</span><span class="sxs-lookup"><span data-stu-id="a860f-103">This sample demonstrates the use and configuration of promoted properties in the SQL workflow instance store.</span></span> <span data-ttu-id="a860f-104">SQL 工作流程執行個體存放區是以 SQL 為基礎的執行個體存放區實作。</span><span class="sxs-lookup"><span data-stu-id="a860f-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="a860f-105">它允許執行個體在 SQL Server 或 SQL Server Express 資料庫中來回儲存及載入其狀態。</span><span class="sxs-lookup"><span data-stu-id="a860f-105">It allows an instance to save its state and load its state to and from a SQL Server or SQL Server Express database.</span></span> <span data-ttu-id="a860f-106">存放區擴充性功能可讓使用者定義儲存在執行個體存放區中的屬性。</span><span class="sxs-lookup"><span data-stu-id="a860f-106">The store extensibility feature allows the user to define properties that are stored in the instance store.</span></span> <span data-ttu-id="a860f-107">這些屬性會顯示在提升屬性檢視表中，供使用者查詢屬性。</span><span class="sxs-lookup"><span data-stu-id="a860f-107">These properties are displayed in a promoted properties view that allows the user to query for them.</span></span>  
  
 <span data-ttu-id="a860f-108">這個範例是由實作計數服務的工作流程所組成。</span><span class="sxs-lookup"><span data-stu-id="a860f-108">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="a860f-109">一旦叫用服務的 Start 方法，服務就會從 0 計數到 29。</span><span class="sxs-lookup"><span data-stu-id="a860f-109">Once the service's start method is invoked, the service counts from 0 to 29.</span></span> <span data-ttu-id="a860f-110">計數器每 2 秒遞增一次。</span><span class="sxs-lookup"><span data-stu-id="a860f-110">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="a860f-111">每次計數後，工作流程會保存。</span><span class="sxs-lookup"><span data-stu-id="a860f-111">After each count, the workflow persists.</span></span> <span data-ttu-id="a860f-112">目前計數器值會儲存在執行個體存放區中做為已提升的屬性。</span><span class="sxs-lookup"><span data-stu-id="a860f-112">The current counter value is stored in the instance store as a promoted property.</span></span>  
  
 <span data-ttu-id="a860f-113">計數工作流程是由工作流程服務主機自我主控的。</span><span class="sxs-lookup"><span data-stu-id="a860f-113">The Counting Workflow is self-hosted by a Workflow Service Host.</span></span> <span data-ttu-id="a860f-114">此程式的 `Main` 方法會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a860f-114">The program's `Main` method performs the following actions:</span></span>  
  
-   <span data-ttu-id="a860f-115">建立主控計數工作流程的工作流程服務主機，以及定義可用來連接至計數工作流程的端點。</span><span class="sxs-lookup"><span data-stu-id="a860f-115">Creates an instance of the Workflow Service Host that hosts the Counting Workflow and defines the endpoints under which the Counting Workflow can be reached.</span></span>  
  
-   <span data-ttu-id="a860f-116">定義 SQL 工作流程執行個體存放區行為，用來設定 SQL 工作流程執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="a860f-116">Defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="a860f-117">此存放區根據指示將 `CountStatus` 視為已提升的屬性。</span><span class="sxs-lookup"><span data-stu-id="a860f-117">The store is instructed to treat `CountStatus` as a promoted property.</span></span>  
  
-   <span data-ttu-id="a860f-118">建立會呼叫計數工作流程 Start 方法的用戶端。</span><span class="sxs-lookup"><span data-stu-id="a860f-118">Creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="a860f-119">一旦程式啟動，計數器會自動開始計數。</span><span class="sxs-lookup"><span data-stu-id="a860f-119">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="a860f-120">請注意，載入執行個體以及設定 SQL 工作流程執行個體存放區可能要花幾秒才能完成。</span><span class="sxs-lookup"><span data-stu-id="a860f-120">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span>  
  
 <span data-ttu-id="a860f-121">若要將計數器值提升為自訂屬性，必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a860f-121">To promote the counter value as a custom property, the following steps must be taken:</span></span>  
  
1.  <span data-ttu-id="a860f-122">`CounterStatus` 類別定義型別為 <xref:System.Activities.Persistence.PersistenceParticipant> 的執行個體例外狀況，通常活動會使用它來供應狀態變數。</span><span class="sxs-lookup"><span data-stu-id="a860f-122">The class `CounterStatus` defines an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span> <span data-ttu-id="a860f-123">`Count` 定義為唯寫值。</span><span class="sxs-lookup"><span data-stu-id="a860f-123">`Count` is defined as a write-only value.</span></span> <span data-ttu-id="a860f-124">當工作流程執行個體達到保存點時，執行個體延伸將 `Count` 屬性儲存至持續性資料集合中。</span><span class="sxs-lookup"><span data-stu-id="a860f-124">When a workflow instance comes to a persistence point, the instance extension saves the `Count` property into the persistence data collection.</span></span>  
  
2.  <span data-ttu-id="a860f-125">在建立執行個體存放區時，透過 `CountStatus` 方法定義新屬性 `store.Promote()`。</span><span class="sxs-lookup"><span data-stu-id="a860f-125">When creating the instance store, a new property, `CountStatus`, is defined through the `store.Promote()` method.</span></span>  
  
3.  <span data-ttu-id="a860f-126">工作流程的 `SaveCounter` 活動將目前計數器值指派至 `Count` 狀態欄位。</span><span class="sxs-lookup"><span data-stu-id="a860f-126">The workflow's `SaveCounter` activity assigns the current counter value to the `Count` status field.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="a860f-127">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="a860f-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="a860f-128">建立執行個體存放區資料庫。</span><span class="sxs-lookup"><span data-stu-id="a860f-128">Create the instance store database.</span></span>  
  
    1.  <span data-ttu-id="a860f-129">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a860f-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="a860f-130">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元中，巡覽至範例目錄 (\WF\Basic\Persistence\SqlStoreExtensibility\CS)，並執行 CreateInstanceStore.cmd。</span><span class="sxs-lookup"><span data-stu-id="a860f-130">Navigate to the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility\CS) and run CreateInstanceStore.cmd in the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="a860f-131">CreateInstanceStore.cmd 指令碼會嘗試在 SQL Server 2008 Express 預設執行個體上建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="a860f-131">The CreateInstanceStore.cmd script attempts to create the database on the default instance of SQL Server 2008 Express.</span></span> <span data-ttu-id="a860f-132">如果您想要在不同的執行個體上安裝資料庫，請修改指令碼。</span><span class="sxs-lookup"><span data-stu-id="a860f-132">If you want to install the database on a different instance, modify the script to do so.</span></span>  
  
2.  <span data-ttu-id="a860f-133">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，並載入 SqlStoreExtensibility.sln 方案，然後按 CTRL+SHIFT+B 加以建置。</span><span class="sxs-lookup"><span data-stu-id="a860f-133">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and load the SqlStoreExtensibility.sln solution and build it by pressing CTRL+SHIFT+B.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="a860f-134">如果在非預設的 SQL Server 執行個體上安裝資料庫，請在建置方案之前，先更新程式碼中的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a860f-134">If you installed the database on a non-default instance of SQL Server, update the connection string in the code prior to building the solution.</span></span>  
  
3.  <span data-ttu-id="a860f-135">瀏覽至專案的 bin 目錄 (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) 中，系統管理員權限執行此範例[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]、 以滑鼠右鍵按一下 SqlStoreExtensibility.exe 並選取 **身分執行系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="a860f-135">Run the sample with administrator privileges by navigating to the project’s bin directory (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], right-clicking SqlStoreExtensibility.exe and selecting **Run as Administrator**.</span></span>  
  
### <a name="to-verify-the-sample-is-working-correctly"></a><span data-ttu-id="a860f-136">若要驗證範例是否正常執行</span><span class="sxs-lookup"><span data-stu-id="a860f-136">To verify the sample is working correctly</span></span>  
  
1.  <span data-ttu-id="a860f-137">若要檢視選取的執行個體資料表的內容中使用 SQL Server Management Studio**資料庫**， **InstanceStore**，然後**System.ServiceModel.Activities.DurableInstancing.InstanceTable**在 [物件總管] 中，以滑鼠右鍵按一下**System.ServiceModel.Activities.DurableInstancing.InstanceTable** ，然後選取**選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="a860f-137">Use SQL Server Management Studio to view the contents of the instance table by selecting **Databases**, **InstanceStore**, and then **System.ServiceModel.Activities.DurableInstancing.InstanceTable** in the Object Explorer, right-click **System.ServiceModel.Activities.DurableInstancing.InstanceTable** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="a860f-138">如需有關 SQL Server Management Studio 的詳細資訊，請參閱[簡介 SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645)</span><span class="sxs-lookup"><span data-stu-id="a860f-138">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645)</span></span>  
  
2.  <span data-ttu-id="a860f-139">觀察列出的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a860f-139">Observe the workflow instances listed.</span></span>  
  
3.  <span data-ttu-id="a860f-140">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元中，執行位於範例目錄 (\WF\Basic\Persistence\SqlStoreExtensibility) 的 QueryInstanceStore.cmd 指令碼。</span><span class="sxs-lookup"><span data-stu-id="a860f-140">In a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run the QueryInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
4.  <span data-ttu-id="a860f-141">觀察下顯示的計數器值**CountStatus**。</span><span class="sxs-lookup"><span data-stu-id="a860f-141">Observe the counter value displayed under **CountStatus**.</span></span>  
  
5.  <span data-ttu-id="a860f-142">執行指令碼數次以查看**CountStats**值變更。</span><span class="sxs-lookup"><span data-stu-id="a860f-142">Run the script a few times to see the **CountStats** value change.</span></span>  
  
6.  <span data-ttu-id="a860f-143">按 Enter 鍵，結束工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="a860f-143">Press ENTER to terminate the workflow application.</span></span>  
  
### <a name="to-uninstall-the-sample"></a><span data-ttu-id="a860f-144">若要解除安裝範例</span><span class="sxs-lookup"><span data-stu-id="a860f-144">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="a860f-145">執行位於範例目錄 (\WF\Basic\Persistence\SqlStoreExtensibility) 的 RemoveInstanceStore.cmd 指令碼，即可移除執行個體存放區資料庫。</span><span class="sxs-lookup"><span data-stu-id="a860f-145">Remove the instance store database by running the RemoveInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a860f-146">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a860f-146">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a860f-147">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a860f-147">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a860f-148">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a860f-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a860f-149">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a860f-149">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a><span data-ttu-id="a860f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a860f-150">See Also</span></span>  
 [<span data-ttu-id="a860f-151">工作流程持續性</span><span class="sxs-lookup"><span data-stu-id="a860f-151">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="a860f-152">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="a860f-152">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="a860f-153">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="a860f-153">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
