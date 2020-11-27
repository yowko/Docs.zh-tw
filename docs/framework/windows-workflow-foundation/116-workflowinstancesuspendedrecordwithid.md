---
title: 116 - WorkflowInstanceSuspendedRecordWithId
ms.date: 03/30/2017
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
ms.openlocfilehash: affc8e889cba6ea02bddaa0a21d7311df624b087
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281751"
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a><span data-ttu-id="cc768-102">116 - WorkflowInstanceSuspendedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="cc768-102">116 - WorkflowInstanceSuspendedRecordWithId</span></span>

## <a name="properties"></a><span data-ttu-id="cc768-103">屬性</span><span class="sxs-lookup"><span data-stu-id="cc768-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc768-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="cc768-104">ID</span></span>|<span data-ttu-id="cc768-105">116</span><span class="sxs-lookup"><span data-stu-id="cc768-105">116</span></span>|  
|<span data-ttu-id="cc768-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="cc768-106">Keywords</span></span>|<span data-ttu-id="cc768-107">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="cc768-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="cc768-108">層級</span><span class="sxs-lookup"><span data-stu-id="cc768-108">Level</span></span>|<span data-ttu-id="cc768-109">資訊</span><span class="sxs-lookup"><span data-stu-id="cc768-109">Information</span></span>|  
|<span data-ttu-id="cc768-110">通路</span><span class="sxs-lookup"><span data-stu-id="cc768-110">Channel</span></span>|<span data-ttu-id="cc768-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="cc768-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cc768-112">描述</span><span class="sxs-lookup"><span data-stu-id="cc768-112">Description</span></span>  

 <span data-ttu-id="cc768-113">此事件是當工作流程執行個體發出 WorkflowInstanceSuspended Record 時，由 ETW 追蹤參與者發出。</span><span class="sxs-lookup"><span data-stu-id="cc768-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cc768-114">訊息</span><span class="sxs-lookup"><span data-stu-id="cc768-114">Message</span></span>  

 <span data-ttu-id="cc768-115">TrackRecord = WorkflowInstanceSuspendedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="cc768-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="cc768-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cc768-116">Details</span></span>  
  
|<span data-ttu-id="cc768-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="cc768-117">Data Item Name</span></span>|<span data-ttu-id="cc768-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="cc768-118">Data Item Type</span></span>|<span data-ttu-id="cc768-119">描述</span><span class="sxs-lookup"><span data-stu-id="cc768-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cc768-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="cc768-120">InstanceId</span></span>|<span data-ttu-id="cc768-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="cc768-121">xs:GUID</span></span>|<span data-ttu-id="cc768-122">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="cc768-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cc768-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="cc768-123">RecordNumber</span></span>|<span data-ttu-id="cc768-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="cc768-124">xs:long</span></span>|<span data-ttu-id="cc768-125">發出之記錄的序號。</span><span class="sxs-lookup"><span data-stu-id="cc768-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="cc768-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="cc768-126">EventTime</span></span>|<span data-ttu-id="cc768-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="cc768-127">xs:dateTime</span></span>|<span data-ttu-id="cc768-128">發出事件時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="cc768-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="cc768-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="cc768-129">ActivityDefinitionId</span></span>|<span data-ttu-id="cc768-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc768-130">xs:string</span></span>|<span data-ttu-id="cc768-131">工作流程中根活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc768-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="cc768-132">州</span><span class="sxs-lookup"><span data-stu-id="cc768-132">State</span></span>|<span data-ttu-id="cc768-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc768-133">xs:string</span></span>|<span data-ttu-id="cc768-134">工作流程的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="cc768-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="cc768-135">註解</span><span class="sxs-lookup"><span data-stu-id="cc768-135">Annotations</span></span>|<span data-ttu-id="cc768-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc768-136">xs:string</span></span>|<span data-ttu-id="cc768-137">加入至此事件中的附註。</span><span class="sxs-lookup"><span data-stu-id="cc768-137">The annotations that were added to this event.</span></span> <span data-ttu-id="cc768-138">這些值會以 a 格式儲存在 xml 元素中 \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> 。</span><span class="sxs-lookup"><span data-stu-id="cc768-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="cc768-139">如果未指定任何批註，則字串會包含 \<items/> 。</span><span class="sxs-lookup"><span data-stu-id="cc768-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="cc768-140">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。</span><span class="sxs-lookup"><span data-stu-id="cc768-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="cc768-141">如果事件大小超過 ETW 限制，則會捨棄注釋並以 ... 取代注釋值來截斷事件。 \<items> \</items></span><span class="sxs-lookup"><span data-stu-id="cc768-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="cc768-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="cc768-142">ProfileName</span></span>|<span data-ttu-id="cc768-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc768-143">xs:string</span></span>|<span data-ttu-id="cc768-144">造成發送這個事件的名稱或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="cc768-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="cc768-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="cc768-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="cc768-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc768-146">xs:string</span></span>|<span data-ttu-id="cc768-147">工作流程定義 ID</span><span class="sxs-lookup"><span data-stu-id="cc768-147">The workflow definition id</span></span>|  
|<span data-ttu-id="cc768-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cc768-148">AppDomain</span></span>|<span data-ttu-id="cc768-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="cc768-149">xs:string</span></span>|<span data-ttu-id="cc768-150">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="cc768-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
