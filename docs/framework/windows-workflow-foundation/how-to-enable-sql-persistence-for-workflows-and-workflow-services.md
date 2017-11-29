---
title: "HOW TO：啟用工作流程與工作流程服務的 SQL 持續性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b06479f1a649e60e141e807db091e207636edef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="1b957-102">HOW TO：啟用工作流程與工作流程服務的 SQL 持續性</span><span class="sxs-lookup"><span data-stu-id="1b957-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="1b957-103">本主題描述如何設定 SQL 工作流程執行個體存放區功能，以程式設計方式或使用組態檔來啟用工作流程與工作流程服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="1b957-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>  
  
 <span data-ttu-id="1b957-104">Windows Server App Fabric 會簡化設定持續性的程序。</span><span class="sxs-lookup"><span data-stu-id="1b957-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="1b957-105">[App Fabric 持續性組態](http://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="1b957-105"> [App Fabric Persistence Configuration](http://go.microsoft.com/fwlink/?LinkId=201204)</span></span>  
  
 <span data-ttu-id="1b957-106">使用 SQL 工作流程執行個體存放區功能之前，請建立一個讓此功能用於保存工作流程執行個體的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b957-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="1b957-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安裝程式會將與 SQL 工作流程執行個體存放區功能相關聯的 SQL 指令碼檔複製至 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1b957-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="1b957-108">針對 SQL Server 2005 或 SQL Server 2008 資料庫執行這些指令碼檔，且這個資料庫可供 SQL 工作流程執行個體存放區用來保存工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b957-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="1b957-109">先執行 SqlWorkflowInstanceStoreSchema.sql 檔，然後再執行 SqlWorkflowInstanceStoreLogic.sql 檔。</span><span class="sxs-lookup"><span data-stu-id="1b957-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b957-110">若要清除持續性資料庫來擁有乾淨的資料庫，請依照下列順序執行 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1b957-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>  
>   
>  1.  <span data-ttu-id="1b957-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="1b957-111">SqlWorkflowInstanceStoreSchema.sql</span></span>  
> 2.  <span data-ttu-id="1b957-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="1b957-112">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1b957-113">如果您並未建立持續性資料庫，則當主機嘗試保存工作流程時，SQL 工作流程執行個體存放區功能就會擲回與下列其中一個相似的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b957-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>  
>   
>  <span data-ttu-id="1b957-114">System.Data.SqlClient.SqlException：找不到預存程序 'System.Activities.DurableInstancing.CreateLockOwner'</span><span class="sxs-lookup"><span data-stu-id="1b957-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>  
  
 <span data-ttu-id="1b957-115">下列各節描述如何使用 SQL 工作流程執行個體存放區啟用工作流程與工作流程服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="1b957-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="1b957-116">屬性的 SQL 工作流程執行個體存放區，請參閱[屬性的 SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="1b957-116"> properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="1b957-117">啟用使用 WorkflowApplication 之自我裝載工作流程的持續性</span><span class="sxs-lookup"><span data-stu-id="1b957-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>  
 <span data-ttu-id="1b957-118">您可以使用 <xref:System.Activities.WorkflowApplication> 物件模型，以程式設計方式啟用使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 之自我裝載工作流程的持續性。</span><span class="sxs-lookup"><span data-stu-id="1b957-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="1b957-119">下列程序包含執行此作業的步驟。</span><span class="sxs-lookup"><span data-stu-id="1b957-119">The following procedure contains steps to do this.</span></span>  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="1b957-120">若要啟用自我裝載工作流程的持續性</span><span class="sxs-lookup"><span data-stu-id="1b957-120">To enable persistence for self-hosted workflows</span></span>  
  
1.  <span data-ttu-id="1b957-121">加入 System.Activites.DurableInstancing.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="1b957-121">Add a reference to System.Activites.DurableInstancing.dll.</span></span>  
  
2.  <span data-ttu-id="1b957-122">在原始程式檔最上方現有的 "using" 陳述式後方，加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="1b957-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  <span data-ttu-id="1b957-123">建構 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 並將它指派給 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 的 <xref:System.Activities.WorkflowApplication>，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="1b957-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1b957-124">依據您的 SQL Server 版本，連接字串伺服器名稱可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="1b957-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
4.  <span data-ttu-id="1b957-125">叫用 <xref:System.Activities.WorkflowApplication.Persist%2A> 物件上的 <xref:System.Activities.WorkflowApplication> 方法以保存工作流程，或叫用 <xref:System.Activities.WorkflowApplication.Unload%2A> 以保存及卸載工作流程。</span><span class="sxs-lookup"><span data-stu-id="1b957-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="1b957-126">您也可以處理由 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 物件引發的 <xref:System.Activities.WorkflowApplication> 事件，並傳回 <xref:System.Activities.PersistableIdleAction.Persist> 的適當 (<xref:System.Activities.PersistableIdleAction.Unload> 或 <xref:System.Activities.PersistableIdleAction>) 成員。</span><span class="sxs-lookup"><span data-stu-id="1b957-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="1b957-127">請參閱[保存工作流程應用程式](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md)範例[持續性](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)啟用持續性工作流程使用的範例<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，而[How to： 建立和執行長時間執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)步驟[入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="1b957-127">See the [Persisting a Workflow Application](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflows using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, and the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="1b957-128">啟用使用 WorkflowServiceHost 之自我裝載工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="1b957-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>  
 <span data-ttu-id="1b957-129">您可以使用 <xref:System.ServiceModel.WorkflowServiceHost> 類別或 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 類別，啟用以程式設計方式使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 之自我裝載工作流程服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="1b957-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="1b957-130">使用 SqlWorkflowInstanceStoreBehavior 類別</span><span class="sxs-lookup"><span data-stu-id="1b957-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>  
 <span data-ttu-id="1b957-131">以下程序包含使用 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 類別以啟用自我裝載工作流程服務之持續性的步驟。</span><span class="sxs-lookup"><span data-stu-id="1b957-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="1b957-132">若要啟用使用 SqlWorkflowInstanceStoreBehavior 的持續性</span><span class="sxs-lookup"><span data-stu-id="1b957-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>  
  
1.  <span data-ttu-id="1b957-133">加入 System.ServiceModel.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="1b957-133">Add a reference to the System.ServiceModel.dll.</span></span>  
  
2.  <span data-ttu-id="1b957-134">在原始程式檔最上方現有的 "using" 陳述式後方，加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="1b957-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  <span data-ttu-id="1b957-135">建立 `WorkflowServiceHost` 的執行個體，並加入工作流程服務的端點。</span><span class="sxs-lookup"><span data-stu-id="1b957-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  <span data-ttu-id="1b957-136">建構 `SqlWorkflowInstanceStoreBehavior` 物件並設定該行為物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1b957-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  <span data-ttu-id="1b957-137">開啟工作流程服務主機。</span><span class="sxs-lookup"><span data-stu-id="1b957-137">Open the workflow service host.</span></span>  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="1b957-138">請參閱[內建組態](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md)範例[持續性](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)啟用持續性工作流程服務使用的範例`SqlWorkflowInstanceStoreBehavior`類別。</span><span class="sxs-lookup"><span data-stu-id="1b957-138">See the [Built-in Configuration](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflow services using the `SqlWorkflowInstanceStoreBehavior` class.</span></span>  
  
### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="1b957-139">使用 DurableInstancingOptions 屬性</span><span class="sxs-lookup"><span data-stu-id="1b957-139">Using the DurableInstancingOptions Property</span></span>  
 <span data-ttu-id="1b957-140">當套用 `SqlWorkflowInstanceStoreBehavior` 時，會將 `DurableInstancingOptions.InstanceStore` 上的 `WorkflowServiceHost` 設定為使用組態值建立的 `SqlWorkflowInstanceStore` 物件。</span><span class="sxs-lookup"><span data-stu-id="1b957-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="1b957-141">您同樣可以使用程式設計方式，在不必使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 類別的情況下，設定 `WorkflowServiceHost` 的 `SqlWorkflowInstanceStoreBehavior` 屬性，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="1b957-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="1b957-142">使用組態檔啟用使用 WorkflowServiceHost 之 WAS 裝載工作流程服務的持續性</span><span class="sxs-lookup"><span data-stu-id="1b957-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>  
 <span data-ttu-id="1b957-143">您可以使用組態檔，啟用自我裝載或 Windows Process Activation Service (WAS) 裝載之工作流程服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="1b957-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="1b957-144">WAS 裝載的工作流程服務會使用 WorkflowServiceHost，如同自我裝載的工作流程服務一樣。</span><span class="sxs-lookup"><span data-stu-id="1b957-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>  
  
 <span data-ttu-id="1b957-145">`SqlWorkflowInstanceStoreBehavior`，服務行為，可讓您輕易變更[SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)透過 XML 組態屬性。</span><span class="sxs-lookup"><span data-stu-id="1b957-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="1b957-146">如果是 WAS 裝載的工作流程服務，請使用 Web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="1b957-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="1b957-147">下列組態範例示範如何使用組態檔中的 `sqlWorkflowInstanceStore` 行為項目來設定 SQL 工作流程執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="1b957-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>  
  
```xml  
<serviceBehaviors>  
    <behavior name="">  
        <sqlWorkflowInstanceStore   
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                    instanceEncodingOption="GZip | None"  
                    instanceCompletionAction="DeleteAll | DeleteNothing"  
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"  
                    hostLockRenewalPeriod="00:00:30"   
                    runnableInstancesDetectionPeriod="00:00:05">  
  
        <sqlWorkflowInstanceStore/>  
    </behavior>  
</serviceBehaviors>  
```  
  
 <span data-ttu-id="1b957-148">如果您並未設定 `connectionString` 或 `connectionStringName` 屬性的值，SQL 工作流程執行個體存放區就會使用預設命名的連接字串 `DefaultSqlWorkflowInstanceStoreConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="1b957-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>  
  
 <span data-ttu-id="1b957-149">當套用 `SqlWorkflowInstanceStoreBehavior` 時，會將 `DurableInstancingOptions.InstanceStore` 上的 `WorkflowServiceHost` 設定為使用組態值建立的 `SqlWorkflowInstanceStore` 物件。</span><span class="sxs-lookup"><span data-stu-id="1b957-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="1b957-150">您同樣可以使用程式設計方式，在不必使用服務行為項目的情況下，搭配 `SqlWorkflowInstanceStore` 來使用 `WorkflowServiceHost`。</span><span class="sxs-lookup"><span data-stu-id="1b957-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="1b957-151">建議您不要將敏感資訊 (例如，使用者名稱和密碼) 儲存在 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="1b957-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="1b957-152">如果要將敏感資訊儲存在 Web.config 檔案中，則應使用檔案系統存取控制清單 (ACL) 來保護存取 Web.config 檔的安全性。</span><span class="sxs-lookup"><span data-stu-id="1b957-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="1b957-153">此外，您可以也保護在組態檔中的組態值中所述[加密組態資訊使用受保護的組態](http://go.microsoft.com/fwlink/?LinkId=178419)。</span><span class="sxs-lookup"><span data-stu-id="1b957-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](http://go.microsoft.com/fwlink/?LinkId=178419).</span></span>  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="1b957-154">與 SQL 工作流程執行個體存放區功能相關的 Machine.config 項目</span><span class="sxs-lookup"><span data-stu-id="1b957-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>  
 <span data-ttu-id="1b957-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安裝會將下列與 SQL 工作流程執行個體存放區功能相關的項目加入至 Machine.config 檔：</span><span class="sxs-lookup"><span data-stu-id="1b957-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>  
  
-   <span data-ttu-id="1b957-156">將以下行為延伸項目加入至 Machine.config 檔，這樣您就可以使用組態檔中的 <`sqlWorkflowInstanceStore`> 服務行為項目來設定服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="1b957-156">Adds the following behavior extension element to the Machine.config file so that you can use the <`sqlWorkflowInstanceStore`> service behavior element in the configuration file to configure persistence for your services.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <extensions>  
                <behaviorExtensions>  
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
                </behaviorExtensions>  
            </extensions>  
        <system.serviceModel>  
    <configuration>  
    ```
