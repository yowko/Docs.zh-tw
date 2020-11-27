---
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.date: 03/30/2017
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
ms.openlocfilehash: 69c0c58de36a7fff916b11deba888b7cef7c626e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285144"
---
# <a name="115---workflowinstanceabortedrecordwithid"></a><span data-ttu-id="cf602-102">115 - WorkflowInstanceAbortedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="cf602-102">115 - WorkflowInstanceAbortedRecordWithId</span></span>

## <a name="properties"></a><span data-ttu-id="cf602-103">屬性</span><span class="sxs-lookup"><span data-stu-id="cf602-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf602-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="cf602-104">ID</span></span>|<span data-ttu-id="cf602-105">115</span><span class="sxs-lookup"><span data-stu-id="cf602-105">115</span></span>|  
|<span data-ttu-id="cf602-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="cf602-106">Keywords</span></span>|<span data-ttu-id="cf602-107">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="cf602-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="cf602-108">層級</span><span class="sxs-lookup"><span data-stu-id="cf602-108">Level</span></span>|<span data-ttu-id="cf602-109">警告</span><span class="sxs-lookup"><span data-stu-id="cf602-109">Warning</span></span>|  
|<span data-ttu-id="cf602-110">通路</span><span class="sxs-lookup"><span data-stu-id="cf602-110">Channel</span></span>|<span data-ttu-id="cf602-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="cf602-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf602-112">描述</span><span class="sxs-lookup"><span data-stu-id="cf602-112">Description</span></span>  

 <span data-ttu-id="cf602-113">此事件是當工作流程執行個體發出 WorkflowInstanceAbortedRecord 時，由 ETW 追蹤參與者發出。</span><span class="sxs-lookup"><span data-stu-id="cf602-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf602-114">訊息</span><span class="sxs-lookup"><span data-stu-id="cf602-114">Message</span></span>  

 <span data-ttu-id="cf602-115">TrackRecord = WorkflowInstanceAbortedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="cf602-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf602-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf602-116">Details</span></span>  
  
|<span data-ttu-id="cf602-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="cf602-117">Data Item Name</span></span>|<span data-ttu-id="cf602-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="cf602-118">Data Item Type</span></span>|<span data-ttu-id="cf602-119">描述</span><span class="sxs-lookup"><span data-stu-id="cf602-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf602-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="cf602-120">InstanceId</span></span>|<span data-ttu-id="cf602-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="cf602-121">xs:GUID</span></span>|<span data-ttu-id="cf602-122">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="cf602-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cf602-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="cf602-123">RecordNumber</span></span>|<span data-ttu-id="cf602-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="cf602-124">xs:long</span></span>|<span data-ttu-id="cf602-125">發出之記錄的序號。</span><span class="sxs-lookup"><span data-stu-id="cf602-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="cf602-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="cf602-126">EventTime</span></span>|<span data-ttu-id="cf602-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="cf602-127">xs:dateTime</span></span>|<span data-ttu-id="cf602-128">發出事件時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="cf602-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="cf602-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="cf602-129">ActivityDefinitionId</span></span>|<span data-ttu-id="cf602-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf602-130">xs:string</span></span>|<span data-ttu-id="cf602-131">工作流程中根活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf602-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="cf602-132">州</span><span class="sxs-lookup"><span data-stu-id="cf602-132">State</span></span>|<span data-ttu-id="cf602-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf602-133">xs:string</span></span>|<span data-ttu-id="cf602-134">工作流程的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="cf602-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="cf602-135">註解</span><span class="sxs-lookup"><span data-stu-id="cf602-135">Annotations</span></span>|<span data-ttu-id="cf602-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf602-136">xs:string</span></span>|<span data-ttu-id="cf602-137">加入至此事件中的附註。</span><span class="sxs-lookup"><span data-stu-id="cf602-137">The annotations that were added to this event.</span></span> <span data-ttu-id="cf602-138">這些值會以 a 格式儲存在 xml 元素中 \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> 。</span><span class="sxs-lookup"><span data-stu-id="cf602-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="cf602-139">如果未指定任何批註，則字串會包含 \<items/> 。</span><span class="sxs-lookup"><span data-stu-id="cf602-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="cf602-140">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。</span><span class="sxs-lookup"><span data-stu-id="cf602-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="cf602-141">如果事件大小超過 ETW 限制，則會捨棄注釋並以 ... 取代注釋值來截斷事件。 \<items> \</items></span><span class="sxs-lookup"><span data-stu-id="cf602-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="cf602-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="cf602-142">ProfileName</span></span>|<span data-ttu-id="cf602-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf602-143">xs:string</span></span>|<span data-ttu-id="cf602-144">造成發送這個事件的名稱或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="cf602-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="cf602-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="cf602-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="cf602-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf602-146">xs:string</span></span>|<span data-ttu-id="cf602-147">工作流程定義 ID</span><span class="sxs-lookup"><span data-stu-id="cf602-147">The workflow definition id</span></span>|  
|<span data-ttu-id="cf602-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cf602-148">AppDomain</span></span>|<span data-ttu-id="cf602-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="cf602-149">xs:string</span></span>|<span data-ttu-id="cf602-150">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="cf602-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
