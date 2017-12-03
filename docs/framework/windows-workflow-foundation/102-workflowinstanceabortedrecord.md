---
title: 102 - WorkflowInstanceAbortedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b229e7889ea2ea387c6e1146712c27b33b21264
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="102---workflowinstanceabortedrecord"></a><span data-ttu-id="b62a9-102">102 - WorkflowInstanceAbortedRecord</span><span class="sxs-lookup"><span data-stu-id="b62a9-102">102 - WorkflowInstanceAbortedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="b62a9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b62a9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b62a9-104">ID</span><span class="sxs-lookup"><span data-stu-id="b62a9-104">Id</span></span>|<span data-ttu-id="b62a9-105">102</span><span class="sxs-lookup"><span data-stu-id="b62a9-105">102</span></span>|  
|<span data-ttu-id="b62a9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b62a9-106">Keywords</span></span>|<span data-ttu-id="b62a9-107">EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="b62a9-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="b62a9-108">層級</span><span class="sxs-lookup"><span data-stu-id="b62a9-108">Level</span></span>|<span data-ttu-id="b62a9-109">警告</span><span class="sxs-lookup"><span data-stu-id="b62a9-109">Warning</span></span>|  
|<span data-ttu-id="b62a9-110">通道</span><span class="sxs-lookup"><span data-stu-id="b62a9-110">Channel</span></span>|<span data-ttu-id="b62a9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b62a9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b62a9-112">描述</span><span class="sxs-lookup"><span data-stu-id="b62a9-112">Description</span></span>  
 <span data-ttu-id="b62a9-113">此事件是當工作流程執行個體發出 WorkflowInstanceAbortedRecord 時，由 ETW 追蹤參與者發出。</span><span class="sxs-lookup"><span data-stu-id="b62a9-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b62a9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b62a9-114">Message</span></span>  
 <span data-ttu-id="b62a9-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="b62a9-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="b62a9-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b62a9-116">Details</span></span>  
  
|<span data-ttu-id="b62a9-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b62a9-117">Data Item Name</span></span>|<span data-ttu-id="b62a9-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b62a9-118">Data Item Type</span></span>|<span data-ttu-id="b62a9-119">描述</span><span class="sxs-lookup"><span data-stu-id="b62a9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b62a9-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b62a9-120">InstanceId</span></span>|<span data-ttu-id="b62a9-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="b62a9-121">xs:GUID</span></span>|<span data-ttu-id="b62a9-122">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="b62a9-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b62a9-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="b62a9-123">RecordNumber</span></span>|<span data-ttu-id="b62a9-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="b62a9-124">xs:long</span></span>|<span data-ttu-id="b62a9-125">發出之記錄的序號。</span><span class="sxs-lookup"><span data-stu-id="b62a9-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="b62a9-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="b62a9-126">EventTime</span></span>|<span data-ttu-id="b62a9-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="b62a9-127">xs:dateTime</span></span>|<span data-ttu-id="b62a9-128">發出事件時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="b62a9-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="b62a9-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b62a9-129">ActivityDefinitionId</span></span>|<span data-ttu-id="b62a9-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62a9-130">xs:string</span></span>|<span data-ttu-id="b62a9-131">工作流程中根活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="b62a9-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="b62a9-132">原因</span><span class="sxs-lookup"><span data-stu-id="b62a9-132">Reason</span></span>|<span data-ttu-id="b62a9-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62a9-133">xs:string</span></span>|<span data-ttu-id="b62a9-134">工作流程中止的原因。</span><span class="sxs-lookup"><span data-stu-id="b62a9-134">The reason the workflow was aborted</span></span>|  
|<span data-ttu-id="b62a9-135">標註</span><span class="sxs-lookup"><span data-stu-id="b62a9-135">Annotations</span></span>|<span data-ttu-id="b62a9-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62a9-136">xs:string</span></span>|<span data-ttu-id="b62a9-137">加入至此事件中的附註。</span><span class="sxs-lookup"><span data-stu-id="b62a9-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="b62a9-138">值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"type ="> annotationValue\</項目 > \< /i >。</span><span class="sxs-lookup"><span data-stu-id="b62a9-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="b62a9-139">如果沒有指定的註釋的字串，包含\<項目 / >。</span><span class="sxs-lookup"><span data-stu-id="b62a9-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="b62a9-140">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。</span><span class="sxs-lookup"><span data-stu-id="b62a9-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="b62a9-141">如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。</span><span class="sxs-lookup"><span data-stu-id="b62a9-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="b62a9-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="b62a9-142">ProfileName</span></span>|<span data-ttu-id="b62a9-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62a9-143">xs:string</span></span>|<span data-ttu-id="b62a9-144">造成發送這個事件的名稱或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="b62a9-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="b62a9-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="b62a9-145">HostReference</span></span>|<span data-ttu-id="b62a9-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62a9-146">xs:string</span></span>|<span data-ttu-id="b62a9-147">若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="b62a9-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="b62a9-148">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName' 範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="b62a9-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="b62a9-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b62a9-149">AppDomain</span></span>|<span data-ttu-id="b62a9-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62a9-150">xs:string</span></span>|<span data-ttu-id="b62a9-151">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b62a9-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
