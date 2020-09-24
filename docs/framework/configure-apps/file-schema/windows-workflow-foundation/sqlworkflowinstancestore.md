---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: d6c86d02e14a38c2a35ba4858c4abfea73268fd8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148707"
---
# \<sqlWorkflowInstanceStore>

<span data-ttu-id="c8ac2-101">可讓您設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 功能的服務行為，該功能支援將工作流程服務執行個體的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-101">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="c8ac2-102">如需這項功能的詳細資訊，請參閱 [SQL 工作流程實例存放區](../../../windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-102">For more information on this feature, see [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sqlWorkflowInstanceStore>**  
  
## <a name="syntax"></a><span data-ttu-id="c8ac2-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8ac2-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String"
                                hostLockRenewalPeriod="TimeSpan"
                                instanceCompletionAction="DeleteNothing/DeleteAll"
                                instanceEncodingAction="None/GZip"
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8ac2-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c8ac2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c8ac2-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8ac2-106">屬性</span><span class="sxs-lookup"><span data-stu-id="c8ac2-106">Attributes</span></span>  
  
|<span data-ttu-id="c8ac2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c8ac2-107">Attribute</span></span>|<span data-ttu-id="c8ac2-108">描述</span><span class="sxs-lookup"><span data-stu-id="c8ac2-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8ac2-109">connectionString</span><span class="sxs-lookup"><span data-stu-id="c8ac2-109">connectionString</span></span>|<span data-ttu-id="c8ac2-110">字串，其中包含用來連接至基礎持續性資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-110">A string that contains a connection string used to connect to an underlying persistence database.</span></span>|  
|<span data-ttu-id="c8ac2-111">connectionStringName</span><span class="sxs-lookup"><span data-stu-id="c8ac2-111">connectionStringName</span></span>|<span data-ttu-id="c8ac2-112">字串，其中包含連接至資料庫伺服器的具名連接字串。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-112">A string that contains a named connection string to the database server.</span></span> <span data-ttu-id="c8ac2-113">命名連接字串的範例是 "DefaultConnectionString"。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-113">An example of a named connection string is "DefaultConnectionString".</span></span>|  
|<span data-ttu-id="c8ac2-114">hostLockRenewalPeriod</span><span class="sxs-lookup"><span data-stu-id="c8ac2-114">hostLockRenewalPeriod</span></span>|<span data-ttu-id="c8ac2-115">指定時間週期的 Timespan 值，在此時間週期內，主機必須更新執行個體上的鎖定。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-115">A Timespan value that specifies the time period in which the host must renew the lock on an instance.</span></span> <span data-ttu-id="c8ac2-116">如果主機未在指定的時間週期內更新鎖定，執行個體就會解除鎖定，且可讓另一個主機執行個體選取。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-116">If the host does not renew the lock in the specified time period, the instance is unlocked and may be picked up by another host.</span></span><br /><br /> <span data-ttu-id="c8ac2-117">卸載工作流程表示會同時保存該工作流程。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-117">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="c8ac2-118">如果將這個屬性設定為零，則會在工作流程閒置之後，立刻保留及卸載工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-118">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="c8ac2-119">將這個屬性設定為 TimeSpan.MaxValue 可有效地停用卸載作業。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-119">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="c8ac2-120">閒置的工作流程執行個體永遠不會卸載。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-120">Idle workflow instances are never unloaded.</span></span>|  
|<span data-ttu-id="c8ac2-121">instanceCompletionAction</span><span class="sxs-lookup"><span data-stu-id="c8ac2-121">instanceCompletionAction</span></span>|<span data-ttu-id="c8ac2-122">這個值會指定工作流程執行個體是否會在工作流程執行個體完成後保留在持續性存放區中，還是會在該時間點刪除。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-122">A value that specifies whether workflow instance data is kept in the persistence store after the workflow instance completes or if it is deleted at that point.</span></span> <span data-ttu-id="c8ac2-123">這個值的型別為 <xref:System.Activities.DurableInstancing.InstanceCompletionAction>。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-123">This value is of type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.</span></span><br /><br /> <span data-ttu-id="c8ac2-124">列舉動作包括在執行個體完成其作業時，刪除持續性存放區中的執行個體資料，或者不刪除持續性存放區中的執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-124">The enumerated actions consist of deleting the instance data from the persistence store or not deleting the instance data from the persistence store, when the instance has completed its operation.</span></span><br /><br /> <span data-ttu-id="c8ac2-125">若在完成後仍保留執行個體，會導致持續性資料庫快速成長，因而影響資料庫的效能。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-125">Keeping instances after completion causes the persistence database to grow rapidly and this affects the performance of the database.</span></span> <span data-ttu-id="c8ac2-126">請設定資料庫清除原則來定期刪除這些記錄，以確保資料庫的效能層級能夠持續滿足您的效能需求。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-126">You should configure a database purge policy to delete these records periodically to ensure that the performance of the database is at the level that satisfy your performance requirements.</span></span>|  
|<span data-ttu-id="c8ac2-127">instanceEncodingOption</span><span class="sxs-lookup"><span data-stu-id="c8ac2-127">instanceEncodingOption</span></span>|<span data-ttu-id="c8ac2-128">這個選用值會指定將資訊儲存在持續性存放區之前，是否要使用 GZip 演算法壓縮執行個體狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-128">An optional value that specifies  whether the instance state information is compressed using the GZip algorithm before the information is saved in the persistence store..</span></span> <span data-ttu-id="c8ac2-129">這個值的型別為 <xref:System.Activities.DurableInstancing.InstanceEncodingOption>。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-129">This value is of type <xref:System.Activities.DurableInstancing.InstanceEncodingOption>.</span></span> <span data-ttu-id="c8ac2-130">這個屬性的可能值是 <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None> ，它不會指定壓縮，而是 <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip> 指定壓縮實例資料並使用 gzip 演算法。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-130">Possible values for this property are <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>, which specifies no compression, and <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>, which specifies that instance data is compressed and uses the gzip algorithm.</span></span>|  
|<span data-ttu-id="c8ac2-131">instanceLockedExceptionAction</span><span class="sxs-lookup"><span data-stu-id="c8ac2-131">instanceLockedExceptionAction</span></span>|<span data-ttu-id="c8ac2-132">這個值可在執行個體目前已由其他主機鎖定，而主機嘗試鎖定執行個體時，指定回應擲回例外狀況所發生的動作。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-132">A value that specifies the action that occurs in response to an exception that is thrown when the host tries to lock an instance because the instance is currently locked by another host.</span></span> <span data-ttu-id="c8ac2-133">這個值的型別為 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-133">This value is of type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.</span></span><br /><br /> <span data-ttu-id="c8ac2-134">此欄位可使用的選項包括：[None]、[Basic Retry] 及 [Aggressive Retry]。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-134">The options allowed for this field are: None, Basic Retry, and Aggressive Retry.</span></span> <span data-ttu-id="c8ac2-135">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-135">The default value is None.</span></span> <span data-ttu-id="c8ac2-136">下列清單提供這三種選項的描述：</span><span class="sxs-lookup"><span data-stu-id="c8ac2-136">The following list provides you with the descriptions for these three options:</span></span><br /><br /> <span data-ttu-id="c8ac2-137">-   無。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-137">-   None.</span></span> <span data-ttu-id="c8ac2-138">服務主機不會嘗試鎖定執行個體，以及傳遞 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 至呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-138">The service host does not attempt to lock the instance and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller.</span></span><br /><span data-ttu-id="c8ac2-139">-基本重試。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-139">-   Basic Retry.</span></span> <span data-ttu-id="c8ac2-140">服務主機以線性重試間隔，重新嘗試鎖定執行個體，並將例外狀況傳遞至位於順序結尾的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-140">The service host reattempts to lock the instance with a linear retry interval and passes the exception to the caller at the end of the sequence.</span></span><br /><span data-ttu-id="c8ac2-141">-積極重試。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-141">-   Aggressive Retry.</span></span> <span data-ttu-id="c8ac2-142">服務主機以指數遞增延遲，重新嘗試鎖定執行個體，並將 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 傳遞至位於順序結尾的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-142">The service host reattempts to lock the instance with an exponentially increasing delay and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller at the end of the sequence.</span></span>|  
|<span data-ttu-id="c8ac2-143">runnableInstancesDetectionPeriod</span><span class="sxs-lookup"><span data-stu-id="c8ac2-143">runnableInstancesDetectionPeriod</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="c8ac2-144">子元素</span><span class="sxs-lookup"><span data-stu-id="c8ac2-144">Child Elements</span></span>  

 <span data-ttu-id="c8ac2-145">無。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8ac2-146">父項目</span><span class="sxs-lookup"><span data-stu-id="c8ac2-146">Parent Elements</span></span>  
  
|<span data-ttu-id="c8ac2-147">項目</span><span class="sxs-lookup"><span data-stu-id="c8ac2-147">Element</span></span>|<span data-ttu-id="c8ac2-148">描述</span><span class="sxs-lookup"><span data-stu-id="c8ac2-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8ac2-149">\<behavior> 次數 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c8ac2-149">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c8ac2-150">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="c8ac2-150">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8ac2-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8ac2-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [<span data-ttu-id="c8ac2-152">SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="c8ac2-152">SQL Workflow Instance Store</span></span>](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
