---
title: "HOW TO：以 WorkflowServiceHost 設定持續性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41211eb1d104e0e540e257cffd4647c6fff9fb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="e2825-102">HOW TO：以 WorkflowServiceHost 設定持續性</span><span class="sxs-lookup"><span data-stu-id="e2825-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="e2825-103">本主題描述如何設定 SQL 工作流程執行個體存放區功能，透過使用組態檔以啟用裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中之工作流程的持續性。</span><span class="sxs-lookup"><span data-stu-id="e2825-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="e2825-104">使用 SQL 工作流程執行個體存放區功能前，您必須建立一個用於保存工作流程執行個體的 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e2825-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e2825-105">[How to： 啟用 SQL 持續性工作流程與工作流程服務](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2825-105"> [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="e2825-106">若要在組態中設定 SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="e2825-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="e2825-107">您可以透過 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 設定 SQL 工作流程執行個體存放區的屬性，這個服務行為可以讓您透過 XML 組態變更設定。</span><span class="sxs-lookup"><span data-stu-id="e2825-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="e2825-108">下列組態範例示範如何使用組態檔中的 <`sqlWorkflowInstanceStore`> 行為項目來設定 SQL 工作流程執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="e2825-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2825-109">如何設定 SQL 工作流程執行個體存放區，請參閱[How to： 啟用 SQL 持續性工作流程與工作流程服務](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2825-109"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2825-110">個別設定 <`sqlWorkflowInstanceStore`> 行為項目，請參閱[SQL 工作流程執行個體存放區](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="e2825-110"> the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="e2825-111">Windows Server App Fabric 會提供它自己的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="e2825-111">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e2825-112">[Windows Server App Fabric 持續性](http://go.microsoft.com/fwlink/?LinkId=193121)。</span><span class="sxs-lookup"><span data-stu-id="e2825-112"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2825-113">上述組態範例會使用簡化的組態。</span><span class="sxs-lookup"><span data-stu-id="e2825-113">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e2825-114">[簡化組態](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e2825-114"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="e2825-115">若要在程式碼中設定 SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="e2825-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="e2825-116">您可以透過 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 設定 SQL 工作流程執行個體存放區的屬性，這個服務行為可以讓您透過程式碼變更設定。</span><span class="sxs-lookup"><span data-stu-id="e2825-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="e2825-117">下列範例示範如何使用程式碼中的 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 行為項目來設定 SQL 工作流程執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="e2825-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2825-118">如何設定 SQL 工作流程執行個體存放區，請參閱[How to： 啟用 SQL 持續性工作流程與工作流程服務](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2825-118"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e2825-119">個別設定<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>行為項目，請參閱[SQL 工作流程執行個體存放區](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="e2825-119"> the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="e2825-120">Windows Server App Fabric 會提供它自己的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="e2825-120">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e2825-121">[Windows Server App Fabric 持續性](http://go.microsoft.com/fwlink/?LinkId=193121)。</span><span class="sxs-lookup"><span data-stu-id="e2825-121"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2825-122">上述組態範例會使用簡化的組態。</span><span class="sxs-lookup"><span data-stu-id="e2825-122">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e2825-123">[簡化組態](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e2825-123"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="e2825-124">如需如何以程式設計方式設定持續性的範例，請參閱[How to： 啟用工作流程和工作流程服務的持續性](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2825-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2825-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2825-125">See Also</span></span>  
 [<span data-ttu-id="e2825-126">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="e2825-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="e2825-127">工作流程持續性</span><span class="sxs-lookup"><span data-stu-id="e2825-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="e2825-128">Windows Server App Fabric 持續性</span><span class="sxs-lookup"><span data-stu-id="e2825-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)
