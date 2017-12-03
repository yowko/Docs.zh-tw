---
title: 119 - WorkflowInstanceUpdatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f58a7c0e3b3122962e79f7f39f0c0f89f374bd10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="119---workflowinstanceupdatedrecord"></a><span data-ttu-id="68a54-102">119 - WorkflowInstanceUpdatedRecord</span><span class="sxs-lookup"><span data-stu-id="68a54-102">119 - WorkflowInstanceUpdatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="68a54-103">屬性</span><span class="sxs-lookup"><span data-stu-id="68a54-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68a54-104">ID</span><span class="sxs-lookup"><span data-stu-id="68a54-104">ID</span></span>|<span data-ttu-id="68a54-105">119</span><span class="sxs-lookup"><span data-stu-id="68a54-105">119</span></span>|  
|<span data-ttu-id="68a54-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="68a54-106">Keywords</span></span>|<span data-ttu-id="68a54-107">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="68a54-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="68a54-108">層級</span><span class="sxs-lookup"><span data-stu-id="68a54-108">Level</span></span>|<span data-ttu-id="68a54-109">資訊</span><span class="sxs-lookup"><span data-stu-id="68a54-109">Information</span></span>|  
|<span data-ttu-id="68a54-110">通道</span><span class="sxs-lookup"><span data-stu-id="68a54-110">Channel</span></span>|<span data-ttu-id="68a54-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="68a54-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68a54-112">描述</span><span class="sxs-lookup"><span data-stu-id="68a54-112">Description</span></span>  
 <span data-ttu-id="68a54-113">當工作流程執行個體更新時，ETW 追蹤參與者就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="68a54-113">This event is emitted by the ETW tracking participant when a workflow instance is updated.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68a54-114">訊息</span><span class="sxs-lookup"><span data-stu-id="68a54-114">Message</span></span>  
 <span data-ttu-id="68a54-115">TrackRecord= WorkflowInstanceUpdatedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、OriginalDefinitionIdentity = %6、UpdatedDefinitionIdentity = %7、Annotations = %8、ProfileName = %9</span><span class="sxs-lookup"><span data-stu-id="68a54-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9</span></span>  
  
## <a name="details"></a><span data-ttu-id="68a54-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="68a54-116">Details</span></span>  
  
|<span data-ttu-id="68a54-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="68a54-117">Data Item Name</span></span>|<span data-ttu-id="68a54-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="68a54-118">Data Item Type</span></span>|<span data-ttu-id="68a54-119">描述</span><span class="sxs-lookup"><span data-stu-id="68a54-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68a54-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="68a54-120">InstanceId</span></span>|<span data-ttu-id="68a54-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="68a54-121">xs:GUID</span></span>|<span data-ttu-id="68a54-122">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="68a54-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="68a54-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="68a54-123">RecordNumber</span></span>|<span data-ttu-id="68a54-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="68a54-124">xs:long</span></span>|<span data-ttu-id="68a54-125">發出之記錄的序號。</span><span class="sxs-lookup"><span data-stu-id="68a54-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="68a54-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="68a54-126">EventTime</span></span>|<span data-ttu-id="68a54-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="68a54-127">xs:dateTime</span></span>|<span data-ttu-id="68a54-128">發出事件時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="68a54-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="68a54-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="68a54-129">ActivityDefinitionId</span></span>|<span data-ttu-id="68a54-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-130">xs:string</span></span>|<span data-ttu-id="68a54-131">工作流程中根活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="68a54-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="68a54-132">狀態</span><span class="sxs-lookup"><span data-stu-id="68a54-132">State</span></span>|<span data-ttu-id="68a54-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-133">xs:string</span></span>|<span data-ttu-id="68a54-134">工作流程的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="68a54-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="68a54-135">OriginalDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="68a54-135">OriginalDefinitionIdentity</span></span>|<span data-ttu-id="68a54-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-136">xs:string</span></span>|<span data-ttu-id="68a54-137">原始工作流程定義 ID</span><span class="sxs-lookup"><span data-stu-id="68a54-137">The original workflow definition id</span></span>|  
|<span data-ttu-id="68a54-138">UpdatedDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="68a54-138">UpdatedDefinitionIdentity</span></span>|<span data-ttu-id="68a54-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-139">xs:string</span></span>|<span data-ttu-id="68a54-140">更新的工作流程定義 ID</span><span class="sxs-lookup"><span data-stu-id="68a54-140">The updated workflow definition id</span></span>|  
|<span data-ttu-id="68a54-141">標註</span><span class="sxs-lookup"><span data-stu-id="68a54-141">Annotations</span></span>|<span data-ttu-id="68a54-142">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-142">xs:string</span></span>|<span data-ttu-id="68a54-143">加入至此事件中的附註。</span><span class="sxs-lookup"><span data-stu-id="68a54-143">The annotations that were added to this event.</span></span> <span data-ttu-id="68a54-144">值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"type ="> annotationValue\</項目 > \< /i >。</span><span class="sxs-lookup"><span data-stu-id="68a54-144">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="68a54-145">如果沒有指定的註釋的字串，包含\<項目 / >。</span><span class="sxs-lookup"><span data-stu-id="68a54-145">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="68a54-146">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。</span><span class="sxs-lookup"><span data-stu-id="68a54-146">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="68a54-147">如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。</span><span class="sxs-lookup"><span data-stu-id="68a54-147">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="68a54-148">ProfileName</span><span class="sxs-lookup"><span data-stu-id="68a54-148">ProfileName</span></span>|<span data-ttu-id="68a54-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-149">xs:string</span></span>|<span data-ttu-id="68a54-150">造成發送這個事件的名稱或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="68a54-150">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="68a54-151">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="68a54-151">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="68a54-152">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-152">xs:string</span></span>|<span data-ttu-id="68a54-153">工作流程定義 ID</span><span class="sxs-lookup"><span data-stu-id="68a54-153">The workflow definition id</span></span>|  
|<span data-ttu-id="68a54-154">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68a54-154">AppDomain</span></span>|<span data-ttu-id="68a54-155">xs:string</span><span class="sxs-lookup"><span data-stu-id="68a54-155">xs:string</span></span>|<span data-ttu-id="68a54-156">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="68a54-156">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
