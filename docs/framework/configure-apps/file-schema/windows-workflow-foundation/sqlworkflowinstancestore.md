---
title: '&lt;sqlWorkflowInstanceStore&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b4b1903182cfa20944d919f57ff1e09e07953b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsqlworkflowinstancestoregt"></a><span data-ttu-id="36f49-102">&lt;sqlWorkflowInstanceStore&gt;</span><span class="sxs-lookup"><span data-stu-id="36f49-102">&lt;sqlWorkflowInstanceStore&gt;</span></span>
<span data-ttu-id="36f49-103">可讓您設定的服務行為<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>功能，支援保存的狀態資訊到 SQL Server 2005 或 SQL Server 2008 資料庫的工作流程服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="36f49-103">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="36f49-104">如需有關這項功能的詳細資訊，請參閱[SQL 工作流程執行個體存放區](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="36f49-104">For more information on this feature, see [SQL Workflow Instance Store](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
<span data-ttu-id="36f49-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="36f49-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="36f49-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="36f49-106">\<behaviors></span></span>  
<span data-ttu-id="36f49-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="36f49-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="36f49-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="36f49-108">\<behavior></span></span>  
<span data-ttu-id="36f49-109">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="36f49-109">\<sqlWorkflowInstanceStore></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f49-110">語法</span><span class="sxs-lookup"><span data-stu-id="36f49-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                honstLockRenewalPeriod="TimeSpan" 
                                instanceCompletionAction="DeleteNothing/DeleteAll" 
                                instanceEncodingAction="None/GZip" 
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36f49-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36f49-111">Attributes and Elements</span></span>  
 <span data-ttu-id="36f49-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="36f49-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36f49-113">屬性</span><span class="sxs-lookup"><span data-stu-id="36f49-113">Attributes</span></span>  
  
|<span data-ttu-id="36f49-114">屬性</span><span class="sxs-lookup"><span data-stu-id="36f49-114">Attribute</span></span>|<span data-ttu-id="36f49-115">說明</span><span class="sxs-lookup"><span data-stu-id="36f49-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36f49-116">connectionString</span><span class="sxs-lookup"><span data-stu-id="36f49-116">connectionString</span></span>|<span data-ttu-id="36f49-117">字串，其中包含用來連接至基礎持續性資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="36f49-117">A string that contains a connection string used to connect to an underlying persistence database.</span></span>|  
|<span data-ttu-id="36f49-118">connectionStringName</span><span class="sxs-lookup"><span data-stu-id="36f49-118">connectionStringName</span></span>|<span data-ttu-id="36f49-119">字串，包含資料庫伺服器的具名的連接字串。</span><span class="sxs-lookup"><span data-stu-id="36f49-119">A string that contains a named connection string to the database server.</span></span> <span data-ttu-id="36f49-120">具名的連接字串的範例是"DefaultConnectionString"。</span><span class="sxs-lookup"><span data-stu-id="36f49-120">An example of a named connection string is "DefaultConnectionString".</span></span>|  
|<span data-ttu-id="36f49-121">honstLockRenewalPeriod</span><span class="sxs-lookup"><span data-stu-id="36f49-121">honstLockRenewalPeriod</span></span>|<span data-ttu-id="36f49-122">指定時間週期的 Timespan 值，在此時間週期內，主機必須更新執行個體上的鎖定。</span><span class="sxs-lookup"><span data-stu-id="36f49-122">A Timespan value that specifies the time period in which the host must renew the lock on an instance.</span></span> <span data-ttu-id="36f49-123">如果主機未在指定的時間週期內更新鎖定，執行個體就會解除鎖定，且可讓另一個主機執行個體選取。</span><span class="sxs-lookup"><span data-stu-id="36f49-123">If the host does not renew the lock in the specified time period, the instance is unlocked and may be picked up by another host.</span></span><br /><br /> <span data-ttu-id="36f49-124">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="36f49-124">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="36f49-125">如果這個屬性設為的零會保存工作流程執行個體，並將其卸載之後立即工作流程變成閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="36f49-125">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="36f49-126">有效地將此屬性設定為 TimeSpan.MaxValue，就會停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="36f49-126">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="36f49-127">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="36f49-127">Idle workflow instances are never unloaded.</span></span>|  
|<span data-ttu-id="36f49-128">instanceCompletionAction</span><span class="sxs-lookup"><span data-stu-id="36f49-128">instanceCompletionAction</span></span>|<span data-ttu-id="36f49-129">這個值會指定工作流程執行個體是否會在工作流程執行個體完成後保留在持續性存放區中，還是會在該時間點刪除。</span><span class="sxs-lookup"><span data-stu-id="36f49-129">A value that specifies whether workflow instance data is kept in the persistence store after the workflow instance completes or if it is deleted at that point.</span></span> <span data-ttu-id="36f49-130">這個值的型別為 <xref:System.Activities.DurableInstancing.InstanceCompletionAction>。</span><span class="sxs-lookup"><span data-stu-id="36f49-130">This value is of type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.</span></span><br /><br /> <span data-ttu-id="36f49-131">列舉動作包括在執行個體完成其作業時，刪除持續性存放區中的執行個體資料，或者不刪除持續性存放區中的執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="36f49-131">The enumerated actions consist of deleting the instance data from the persistence store or not deleting the instance data from the persistence store, when the instance has completed its operation.</span></span><br /><br /> <span data-ttu-id="36f49-132">若在完成後仍保留執行個體，會導致持續性資料庫快速成長，因而影響資料庫的效能。</span><span class="sxs-lookup"><span data-stu-id="36f49-132">Keeping instances after completion causes the persistence database to grow rapidly and this affects the performance of the database.</span></span> <span data-ttu-id="36f49-133">請設定資料庫清除原則來定期刪除這些記錄，以確保資料庫的效能層級能夠持續滿足您的效能需求。</span><span class="sxs-lookup"><span data-stu-id="36f49-133">You should configure a database purge policy to delete these records periodically to ensure that the performance of the database is at the level that satisfy your performance requirements.</span></span>|  
|<span data-ttu-id="36f49-134">instanceEncodingOption</span><span class="sxs-lookup"><span data-stu-id="36f49-134">instanceEncodingOption</span></span>|<span data-ttu-id="36f49-135">這個選用值會指定將資訊儲存在持續性存放區之前，是否要使用 GZip 演算法壓縮執行個體狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="36f49-135">An optional value that specifies  whether the instance state information is compressed using the GZip algorithm before the information is saved in the persistence store..</span></span> <span data-ttu-id="36f49-136">這個值的型別為 `System.Activities.DurableInstancing.InstanceEncodingAction`。</span><span class="sxs-lookup"><span data-stu-id="36f49-136">This value is of type `System.Activities.DurableInstancing.InstanceEncodingAction`.</span></span> <span data-ttu-id="36f49-137">這個屬性的可能值為"None"，其指定未壓縮和"GZip"，指定資料壓縮，並使用 gzip 演算法，該執行個體。</span><span class="sxs-lookup"><span data-stu-id="36f49-137">Possible values for this property are "None", which specifies no compression, and "GZip", which specifies that instance data is compressed and uses the gzip algorithm.</span></span>|  
|<span data-ttu-id="36f49-138">instanceLockedExceptionAction</span><span class="sxs-lookup"><span data-stu-id="36f49-138">instanceLockedExceptionAction</span></span>|<span data-ttu-id="36f49-139">這個值可在執行個體目前已由其他主機鎖定，而主機嘗試鎖定執行個體時，指定回應擲回例外狀況所發生的動作。</span><span class="sxs-lookup"><span data-stu-id="36f49-139">A value that specifies the action that occurs in response to an exception that is thrown when the host tries to lock an instance because the instance is currently locked by another host.</span></span> <span data-ttu-id="36f49-140">這個值的型別為 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="36f49-140">This value is of type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.</span></span><br /><br /> <span data-ttu-id="36f49-141">此欄位可使用的選項包括：[None]、[Basic Retry] 及 [Aggressive Retry]。</span><span class="sxs-lookup"><span data-stu-id="36f49-141">The options allowed for this field are: None, Basic Retry, and Aggressive Retry.</span></span> <span data-ttu-id="36f49-142">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="36f49-142">The default value is None.</span></span> <span data-ttu-id="36f49-143">下列清單提供這三種選項的描述：</span><span class="sxs-lookup"><span data-stu-id="36f49-143">The following list provides you with the descriptions for these three options:</span></span><br /><br /> <span data-ttu-id="36f49-144">-   無。</span><span class="sxs-lookup"><span data-stu-id="36f49-144">-   None.</span></span> <span data-ttu-id="36f49-145">服務主機不會嘗試鎖定執行個體，以及傳遞 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 至呼叫端。</span><span class="sxs-lookup"><span data-stu-id="36f49-145">The service host does not attempt to lock the instance and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller.</span></span><br /><span data-ttu-id="36f49-146">-Basic Retry。</span><span class="sxs-lookup"><span data-stu-id="36f49-146">-   Basic Retry.</span></span> <span data-ttu-id="36f49-147">服務主機以線性重試間隔，重新嘗試鎖定執行個體，並將例外狀況傳遞至位於順序結尾的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="36f49-147">The service host reattempts to lock the instance with a linear retry interval and passes the exception to the caller at the end of the sequence.</span></span><br /><span data-ttu-id="36f49-148">-積極重試。</span><span class="sxs-lookup"><span data-stu-id="36f49-148">-   Aggressive Retry.</span></span> <span data-ttu-id="36f49-149">服務主機以指數遞增延遲，重新嘗試鎖定執行個體，並將 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 傳遞至位於順序結尾的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="36f49-149">The service host reattempts to lock the instance with an exponentially increasing delay and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller at the end of the sequence.</span></span>|  
|<span data-ttu-id="36f49-150">runnableInstancesDetectionPeriod</span><span class="sxs-lookup"><span data-stu-id="36f49-150">runnableInstancesDetectionPeriod</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="36f49-151">子元素</span><span class="sxs-lookup"><span data-stu-id="36f49-151">Child Elements</span></span>  
 <span data-ttu-id="36f49-152">無。</span><span class="sxs-lookup"><span data-stu-id="36f49-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36f49-153">父項目</span><span class="sxs-lookup"><span data-stu-id="36f49-153">Parent Elements</span></span>  
  
|<span data-ttu-id="36f49-154">項目</span><span class="sxs-lookup"><span data-stu-id="36f49-154">Element</span></span>|<span data-ttu-id="36f49-155">說明</span><span class="sxs-lookup"><span data-stu-id="36f49-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36f49-156">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="36f49-156">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="36f49-157">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="36f49-157">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36f49-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36f49-158">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
 [<span data-ttu-id="36f49-159">SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="36f49-159">SQL Workflow Instance Store</span></span>](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
