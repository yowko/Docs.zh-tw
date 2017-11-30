---
title: 114 - WorkflowInstanceRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57eab386e8d0486caa98a6e2f3d2f72e9e89fab7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="114---workflowinstancerecordwithid"></a><span data-ttu-id="201d6-102">114 - WorkflowInstanceRecordWithId</span><span class="sxs-lookup"><span data-stu-id="201d6-102">114 - WorkflowInstanceRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="201d6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="201d6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="201d6-104">ID</span><span class="sxs-lookup"><span data-stu-id="201d6-104">ID</span></span>|<span data-ttu-id="201d6-105">114</span><span class="sxs-lookup"><span data-stu-id="201d6-105">114</span></span>|  
|<span data-ttu-id="201d6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="201d6-106">Keywords</span></span>|<span data-ttu-id="201d6-107">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="201d6-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="201d6-108">層級</span><span class="sxs-lookup"><span data-stu-id="201d6-108">Level</span></span>|<span data-ttu-id="201d6-109">資訊</span><span class="sxs-lookup"><span data-stu-id="201d6-109">Information</span></span>|  
|<span data-ttu-id="201d6-110">通道</span><span class="sxs-lookup"><span data-stu-id="201d6-110">Channel</span></span>|<span data-ttu-id="201d6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="201d6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="201d6-112">描述</span><span class="sxs-lookup"><span data-stu-id="201d6-112">Description</span></span>  
 <span data-ttu-id="201d6-113">此事件是當工作流程執行個體發出 WorkflowInstanceRecord 工作流程狀態：Resumed、Persisted、Idle、Deleted、Completed、Canceled、Unloaded 與 Unsuspended 時，由 ETW 追蹤參與者發出。</span><span class="sxs-lookup"><span data-stu-id="201d6-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="201d6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="201d6-114">Message</span></span>  
 <span data-ttu-id="201d6-115">TrackRecord= WorkflowInstanceRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="201d6-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="201d6-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="201d6-116">Details</span></span>  
  
|<span data-ttu-id="201d6-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="201d6-117">Data Item Name</span></span>|<span data-ttu-id="201d6-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="201d6-118">Data Item Type</span></span>|<span data-ttu-id="201d6-119">描述</span><span class="sxs-lookup"><span data-stu-id="201d6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="201d6-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="201d6-120">InstanceId</span></span>|<span data-ttu-id="201d6-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="201d6-121">xs:GUID</span></span>|<span data-ttu-id="201d6-122">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="201d6-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="201d6-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="201d6-123">RecordNumber</span></span>|<span data-ttu-id="201d6-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="201d6-124">xs:long</span></span>|<span data-ttu-id="201d6-125">發出之記錄的序號。</span><span class="sxs-lookup"><span data-stu-id="201d6-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="201d6-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="201d6-126">EventTime</span></span>|<span data-ttu-id="201d6-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="201d6-127">xs:dateTime</span></span>|<span data-ttu-id="201d6-128">發出事件時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="201d6-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="201d6-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="201d6-129">ActivityDefinitionId</span></span>|<span data-ttu-id="201d6-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="201d6-130">xs:string</span></span>|<span data-ttu-id="201d6-131">工作流程中根活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="201d6-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="201d6-132">狀態</span><span class="sxs-lookup"><span data-stu-id="201d6-132">State</span></span>|<span data-ttu-id="201d6-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="201d6-133">xs:string</span></span>|<span data-ttu-id="201d6-134">工作流程的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="201d6-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="201d6-135">標註</span><span class="sxs-lookup"><span data-stu-id="201d6-135">Annotations</span></span>|<span data-ttu-id="201d6-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="201d6-136">xs:string</span></span>|<span data-ttu-id="201d6-137">加入至此事件中的附註。</span><span class="sxs-lookup"><span data-stu-id="201d6-137">The annotations that were added to this event.</span></span> <span data-ttu-id="201d6-138">值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"type ="> annotationValue\</項目 > \< /i >。</span><span class="sxs-lookup"><span data-stu-id="201d6-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="201d6-139">如果沒有指定的註釋的字串，包含\<項目 / >。</span><span class="sxs-lookup"><span data-stu-id="201d6-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="201d6-140">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。</span><span class="sxs-lookup"><span data-stu-id="201d6-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="201d6-141">如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。</span><span class="sxs-lookup"><span data-stu-id="201d6-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="201d6-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="201d6-142">ProfileName</span></span>|<span data-ttu-id="201d6-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="201d6-143">xs:string</span></span>|<span data-ttu-id="201d6-144">造成發送這個事件的名稱或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="201d6-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="201d6-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="201d6-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="201d6-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="201d6-146">xs:string</span></span>|<span data-ttu-id="201d6-147">工作流程定義 ID</span><span class="sxs-lookup"><span data-stu-id="201d6-147">The workflow definition id</span></span>|  
|<span data-ttu-id="201d6-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="201d6-148">AppDomain</span></span>|<span data-ttu-id="201d6-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="201d6-149">xs:string</span></span>|<span data-ttu-id="201d6-150">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="201d6-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
