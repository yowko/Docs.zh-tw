---
title: 內建組態
ms.date: 03/30/2017
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
ms.openlocfilehash: e76c019d9fc1b416e6fa8175a70b5fd01d9ff53e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867838"
---
# <a name="built-in-configuration"></a><span data-ttu-id="46e47-102">內建組態</span><span class="sxs-lookup"><span data-stu-id="46e47-102">Built-in Configuration</span></span>
<span data-ttu-id="46e47-103">這個範例示範使用和設定 SQL 工作流程執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="46e47-103">This sample demonstrates the use and configuration of the SQL workflow instance store.</span></span> <span data-ttu-id="46e47-104">SQL 工作流程執行個體存放區是以 SQL 為基礎的執行個體存放區實作。</span><span class="sxs-lookup"><span data-stu-id="46e47-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="46e47-105">它允許執行個體在 SQL Server 或 SQL Server Express 資料庫中來回儲存及載入。</span><span class="sxs-lookup"><span data-stu-id="46e47-105">It allows an instance to save and load its state to and from a SQL Server or SQL Server Express database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46e47-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="46e47-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="46e47-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="46e47-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46e47-108">如果此目錄不存在，請移至 （下載頁面） 以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="46e47-108">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46e47-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="46e47-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="46e47-110">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="46e47-110">Sample Details</span></span>  
 <span data-ttu-id="46e47-111">這個範例是由實作計數服務的工作流程所組成。</span><span class="sxs-lookup"><span data-stu-id="46e47-111">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="46e47-112">一旦叫用服務的 Start 方法，服務就會從 0 計數到 59。</span><span class="sxs-lookup"><span data-stu-id="46e47-112">Once the service's start method is invoked, the service counts from 0 to 59.</span></span> <span data-ttu-id="46e47-113">計數器每 2 秒遞增一次。</span><span class="sxs-lookup"><span data-stu-id="46e47-113">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="46e47-114">每次計數後，工作流程會保存。</span><span class="sxs-lookup"><span data-stu-id="46e47-114">After each count, the workflow persists.</span></span>  
  
 <span data-ttu-id="46e47-115">計數工作流程是由工作流程服務主機自我主控的。</span><span class="sxs-lookup"><span data-stu-id="46e47-115">The counting workflow is self-hosted by a workflow service host.</span></span> <span data-ttu-id="46e47-116">程式的 `Main` 方法會建立裝載計數工作流程之工作流程服務主機的執行個體。</span><span class="sxs-lookup"><span data-stu-id="46e47-116">The program's `Main` method creates an instance of the workflow service host that hosts the counting workflow.</span></span> <span data-ttu-id="46e47-117">它會定義可用來連接至計數工作流程的端點。</span><span class="sxs-lookup"><span data-stu-id="46e47-117">It defines the endpoints under which the counting workflow can be reached.</span></span> <span data-ttu-id="46e47-118">定義端點之後，它會定義 SQL 工作流程執行個體存放區行為，用來設定 SQL 工作流程執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="46e47-118">After that, it defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="46e47-119">接著程式會建立呼叫計數工作流程 Start 方法的用戶端。</span><span class="sxs-lookup"><span data-stu-id="46e47-119">Next, the program creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="46e47-120">一旦程式啟動，計數器會自動開始計數。</span><span class="sxs-lookup"><span data-stu-id="46e47-120">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="46e47-121">請注意，載入執行個體以及設定 SQL 工作流程執行個體存放區可能要花幾秒才能完成。</span><span class="sxs-lookup"><span data-stu-id="46e47-121">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span> <span data-ttu-id="46e47-122">如需有關工作流程執行個體存放區的詳細資訊，請參閱 < [SQL 工作流程執行個體存放區](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="46e47-122">For more information about the workflow instance store, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
 <span data-ttu-id="46e47-123">此範例包含二個部分：</span><span class="sxs-lookup"><span data-stu-id="46e47-123">The sample consists of two parts:</span></span>  
  
1.  <span data-ttu-id="46e47-124">InstanceStore1 示範如何使用 C# 程式碼設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> (請參閱 Program.cs)。</span><span class="sxs-lookup"><span data-stu-id="46e47-124">InstanceStore1 shows how <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is configured using C# code (see Program.cs).</span></span>  
  
2.  <span data-ttu-id="46e47-125">InstanceStore2 示範如何使用 XML 設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> (請參閱 App.config)。</span><span class="sxs-lookup"><span data-stu-id="46e47-125">InstanceStore2 shows how <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is configured using XML (see App.config).</span></span>  
  
 <span data-ttu-id="46e47-126">以下為可用來設定 SQL 工作流程執行個體存放區行為的設定：</span><span class="sxs-lookup"><span data-stu-id="46e47-126">The following settings are available to configure the SQL Workflow Instance Store behavior:</span></span>  
  
-   <span data-ttu-id="46e47-127">設定 `HostLockRenewalPeriod`。</span><span class="sxs-lookup"><span data-stu-id="46e47-127">Set the `HostLockRenewalPeriod`.</span></span> <span data-ttu-id="46e47-128">這個時間會定義時間間隔，用於主機更新其執行之執行個體的擁有權鎖定。</span><span class="sxs-lookup"><span data-stu-id="46e47-128">This time defines the interval with which the host renews the ownership lock of the instances it runs.</span></span> <span data-ttu-id="46e47-129">鎖定資訊儲存在執行個體存放區中。</span><span class="sxs-lookup"><span data-stu-id="46e47-129">The lock information is stored in the Instance Store.</span></span> <span data-ttu-id="46e47-130">如果擁有權連續兩次未在 `HostLockRenewalPeriod` 中定義的時間間隔更新，則會將執行個體視為已放棄。</span><span class="sxs-lookup"><span data-stu-id="46e47-130">If the ownership is not renewed for two of the intervals defined in `HostLockRenewalPeriod`, the instance is considered abandoned.</span></span> <span data-ttu-id="46e47-131">如果另一個 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 正在執行相同的工作流程，並且連接至相同的執行個體存放區 (在同一部或不同部電腦上)，則會復原該執行個體。</span><span class="sxs-lookup"><span data-stu-id="46e47-131">If another <xref:System.ServiceModel.Activities.WorkflowServiceHost> is running the same workflow and connected to the same instance store (either on the same computer or a different computer), it recovers that instance.</span></span> <span data-ttu-id="46e47-132">(執行個體復原不在本範例的範圍內)。</span><span class="sxs-lookup"><span data-stu-id="46e47-132">(Instance Recovery is out of scope for this sample.)</span></span>  
  
-   <span data-ttu-id="46e47-133">設定 `RunnableInstancesDetectionPeriod`。</span><span class="sxs-lookup"><span data-stu-id="46e47-133">Set the `RunnableInstancesDetectionPeriod`.</span></span> <span data-ttu-id="46e47-134">這段時間定義主機輪詢可執行之執行個體的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="46e47-134">This period defines the interval in which the host polls for instances that have become runnable.</span></span> <span data-ttu-id="46e47-135">執行個體在下列任何事件發生時會變成可執行：</span><span class="sxs-lookup"><span data-stu-id="46e47-135">Instances may become runnable if any of the following events occur:</span></span>  
  
    -   <span data-ttu-id="46e47-136">永久性計時器 (<xref:System.Activities.Statements.Delay>) 過期。</span><span class="sxs-lookup"><span data-stu-id="46e47-136">A Durable Timer (<xref:System.Activities.Statements.Delay>) expires.</span></span>  
  
    -   <span data-ttu-id="46e47-137">另一部主機遺失其 `HostLockRenewal` 活動訊號 (例如，因為電腦當機) 且執行個體已復原。</span><span class="sxs-lookup"><span data-stu-id="46e47-137">Another host misses its `HostLockRenewal` heartbeat (for example, due to a computer crash) and the instance is recovered.</span></span>  
  
-   <span data-ttu-id="46e47-138">設定 `InstanceCompletionAction`。</span><span class="sxs-lookup"><span data-stu-id="46e47-138">Set the `InstanceCompletionAction`.</span></span> <span data-ttu-id="46e47-139">如果這個屬性設為 `DeleteNothing`，就會在執行個體存放區中保存完整的執行個體；如果設為 `DeleteAll`，則會在完成時從存放區中刪除執行個體。</span><span class="sxs-lookup"><span data-stu-id="46e47-139">This property, if set to `DeleteNothing`, keeps completed instances in the Instance Store; if set to `DeleteAll`, instances are deleted from the store upon completion.</span></span> <span data-ttu-id="46e47-140">請注意</span><span class="sxs-lookup"><span data-stu-id="46e47-140">Note that</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46e47-141">在計時完成之前按下 ENTER 終止主機，並不會完成工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="46e47-141">Terminating the host by pressing ENTER before the counting has completed does not complete the workflow instance.</span></span>  
  
-   <span data-ttu-id="46e47-142">設定 `InstanceLockedExceptionAction`。</span><span class="sxs-lookup"><span data-stu-id="46e47-142">Set the `InstanceLockedExceptionAction`.</span></span> <span data-ttu-id="46e47-143">這個設定會定義主機想要載入另一部主機鎖定的執行個體時，應該怎麼做。</span><span class="sxs-lookup"><span data-stu-id="46e47-143">This setting defines what a host should do if it wants to load an instance that is locked by another host.</span></span> <span data-ttu-id="46e47-144">以下為可行的選項：</span><span class="sxs-lookup"><span data-stu-id="46e47-144">The following options exist:</span></span>  
  
    -   <span data-ttu-id="46e47-145">如果設為 `NoRetry`：不重試載入並將 `InstanceLockedException` 傳回至主機。</span><span class="sxs-lookup"><span data-stu-id="46e47-145">If set to `NoRetry`: Do not retry the load and return an `InstanceLockedException` to the host.</span></span>  
  
    -   <span data-ttu-id="46e47-146">如果設為 `BasicRetry`：繼續重試載入執行個體。</span><span class="sxs-lookup"><span data-stu-id="46e47-146">If set to `BasicRetry`: Keep retrying to load the instance.</span></span> <span data-ttu-id="46e47-147">重試是根據簡單的線性演算法排程 (例如，每 5 秒重試一次)。</span><span class="sxs-lookup"><span data-stu-id="46e47-147">The retries are scheduled according to a simple linear algorithm (for example, retry every 5 seconds).</span></span>  
  
    -   <span data-ttu-id="46e47-148">如果設為 `AggressiveRetry`：繼續重試載入執行個體。</span><span class="sxs-lookup"><span data-stu-id="46e47-148">If set to `AggressiveRetry`: Keep retrying to load the instance.</span></span> <span data-ttu-id="46e47-149">重試是根據主動指數後退演算法 (Aggressive Exponential Back-off Algorithm) 排程。</span><span class="sxs-lookup"><span data-stu-id="46e47-149">The retries are scheduled according to an aggressive exponential back-off algorithm.</span></span>  
  
-   <span data-ttu-id="46e47-150">設定編碼選項。</span><span class="sxs-lookup"><span data-stu-id="46e47-150">Set the Encoding option.</span></span> <span data-ttu-id="46e47-151">這個設定會定義執行個體狀態儲存在 SQL 工作流程執行個體存放區中的方式。</span><span class="sxs-lookup"><span data-stu-id="46e47-151">This setting defines how the instance state is stored in the SQL Workflow Instance Store.</span></span> <span data-ttu-id="46e47-152">以下為可行的選項：</span><span class="sxs-lookup"><span data-stu-id="46e47-152">The following options exist:</span></span>  
  
    -   <span data-ttu-id="46e47-153">執行個體狀態是使用 GZip 壓縮演算法進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="46e47-153">The instance state is compressed using the GZip compression algorithm.</span></span>  
  
    -   <span data-ttu-id="46e47-154">執行個體狀態不會經過壓縮。</span><span class="sxs-lookup"><span data-stu-id="46e47-154">The instance state is not compressed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="46e47-155">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="46e47-155">To use this sample</span></span>  
  
1.  <span data-ttu-id="46e47-156">以系統管理員身分開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元 (如果有權限可以使用的話)。</span><span class="sxs-lookup"><span data-stu-id="46e47-156">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt as an Administrator if permissions are available.</span></span>  
  
2.  <span data-ttu-id="46e47-157">巡覽至範例目錄 (\WF\Basic\Persistence\BuiltInConfiguration\CS)，並執行 CreateInstanceStore.cmd。</span><span class="sxs-lookup"><span data-stu-id="46e47-157">Navigate to the sample directory (\WF\Basic\Persistence\BuiltInConfiguration\CS) and run CreateInstanceStore.cmd.</span></span>  
  
3.  <span data-ttu-id="46e47-158">如果未提供系統管理員權限，請建立 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="46e47-158">If Administrator privileges are not available, Create SQL Server login.</span></span> <span data-ttu-id="46e47-159">移至`Security`，**登入**。</span><span class="sxs-lookup"><span data-stu-id="46e47-159">Go to `Security`, **Logins**.</span></span> <span data-ttu-id="46e47-160">以滑鼠右鍵按一下**登入**並建立新的登入。</span><span class="sxs-lookup"><span data-stu-id="46e47-160">Right-click **Logins** and create a new login.</span></span>  
  
4.  <span data-ttu-id="46e47-161">將 ACL 使用者加入至 SQL 角色。</span><span class="sxs-lookup"><span data-stu-id="46e47-161">Add your ACL user to SQL role.</span></span> <span data-ttu-id="46e47-162">開啟**資料庫**， **InstanceStore**，**安全性**。</span><span class="sxs-lookup"><span data-stu-id="46e47-162">Open **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="46e47-163">以滑鼠右鍵按一下**使用者**，然後選取**新手**。</span><span class="sxs-lookup"><span data-stu-id="46e47-163">Right-click **Users** and select **New users**.</span></span> <span data-ttu-id="46e47-164">設定**登入名稱**上一個步驟中建立的使用者。</span><span class="sxs-lookup"><span data-stu-id="46e47-164">Set the **Login name** to the user created in the previous step.</span></span> <span data-ttu-id="46e47-165">將使用者新增至資料庫角色成員資格**System.Activities.DurableInstancing.InstanceStoreUsers** （以及其他）。</span><span class="sxs-lookup"><span data-stu-id="46e47-165">Add the user to the Database role membership **System.Activities.DurableInstancing.InstanceStoreUsers** (and others).</span></span> <span data-ttu-id="46e47-166">請注意，使用者可能已存在 (例如 dbo 使用者)。</span><span class="sxs-lookup"><span data-stu-id="46e47-166">Note that the user might exist already (for example, user dbo).</span></span>  
  
5.  <span data-ttu-id="46e47-167">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 InstanceStore.sln 檔案，然後按 CTRL+SHIFT+B 建置方案。</span><span class="sxs-lookup"><span data-stu-id="46e47-167">Open the InstanceStore.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="46e47-168">在  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]、 瀏覽至範例的適當 bin\debug 目錄 (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug)、 以滑鼠右鍵按一下 InstanceStore.exe 和選取**以系統管理員身分**.</span><span class="sxs-lookup"><span data-stu-id="46e47-168">In [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the sample’s appropriate bin\debug directory (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), right click InstanceStore.exe and select **Run as administrator**.</span></span> <span data-ttu-id="46e47-169">這個範例必須以系統管理權限執行，因為它會開啟通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="46e47-169">This sample must be run with administrative privileges because it opens a channel listener.</span></span>  
  
7.  <span data-ttu-id="46e47-170">如果您在 SQL Server Express 的本機安裝以外的資料庫中建立了執行個體存放區，則必須更新範例中的資料庫連接字串 (InstanceStore1 專案的 Program.cs 中為 `const string ConnectionString`，InstanceStore2 專案的 App.config 中為 `connectionString` 屬性)，並且重新編譯範例。</span><span class="sxs-lookup"><span data-stu-id="46e47-170">If you created the instance store in a database other than a local installation of SQL Server Express you must update the database connection string (`const string ConnectionString` in Program.cs of the InstanceStore1 project, and the `connectionString` attribute in App.config of the InstanceStore2 project) in the sample and recompile the sample.</span></span>  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a><span data-ttu-id="46e47-171">若要驗證範例是否正常執行</span><span class="sxs-lookup"><span data-stu-id="46e47-171">To verify the sample is running correctly</span></span>  
  
1.  <span data-ttu-id="46e47-172">在範例正在執行時，啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="46e47-172">While the sample is running, start SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="46e47-173">在 [**物件總管] 中**，選取**資料庫**， **InstanceStore**，**資料表**，然後**System.Activities.DurableInstancing.InstanceTable**。</span><span class="sxs-lookup"><span data-stu-id="46e47-173">In the **Object Explorer**, select **Databases**, **InstanceStore**, **Tables**, and then **System.Activities.DurableInstancing.InstanceTable**.</span></span>  
  
3.  <span data-ttu-id="46e47-174">以滑鼠右鍵按一下**InstanceTable** ，然後選取**選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="46e47-174">Right click **InstanceTable** and select **Select Top 1000 Rows**.</span></span>  
  
4.  <span data-ttu-id="46e47-175">觀察有新的項目，且**鎖定到期**變更每隔 5 秒 (按一下工作列上的**Execute**按鈕以重新整理查詢)。</span><span class="sxs-lookup"><span data-stu-id="46e47-175">Observe that there is a new entry and that the **Lock Expiration** changes every 5 seconds, (click the taskbar’s **Execute** button to refresh the query).</span></span> <span data-ttu-id="46e47-176">這是設定的結果**Host Lock Renewal Period**為 5。</span><span class="sxs-lookup"><span data-stu-id="46e47-176">This is a consequence of setting the **Host Lock Renewal Period** to 5.</span></span>  
  
5.  <span data-ttu-id="46e47-177">在計時完成之後，您會看見執行個體表中該項目已移除。</span><span class="sxs-lookup"><span data-stu-id="46e47-177">Observe after the counting completes, that the entry in the instance table is removed.</span></span> <span data-ttu-id="46e47-178">這是設定的結果**執行個體完成動作**要**DeleteAll**。</span><span class="sxs-lookup"><span data-stu-id="46e47-178">This is a consequence of setting **Instance Completion Action** to **DeleteAll**.</span></span>  
  
6.  <span data-ttu-id="46e47-179">按下 ENTER 終止工作流程主應用程式，並觀察**LockOwnersTable**會被刪除。</span><span class="sxs-lookup"><span data-stu-id="46e47-179">Press ENTER to terminate the workflow host application and observe that the **LockOwnersTable** is deleted.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="46e47-180">若要解除安裝範例</span><span class="sxs-lookup"><span data-stu-id="46e47-180">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="46e47-181">執行範例目錄 (\WF\Basic\Persistence\BuiltInConfiguration) 中的 RemoveInstanceStore.cmd。</span><span class="sxs-lookup"><span data-stu-id="46e47-181">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\BuiltInConfiguration).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46e47-182">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="46e47-182">The samples may already be installed on your computer.</span></span> <span data-ttu-id="46e47-183">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="46e47-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46e47-184">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="46e47-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46e47-185">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="46e47-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a><span data-ttu-id="46e47-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46e47-186">See Also</span></span>  
 [<span data-ttu-id="46e47-187">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="46e47-187">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
