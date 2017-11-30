---
title: 112 - WorkflowInstanceSuspendedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc825c7c-8c90-48f7-9336-9a978a8246c6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc10a7c7a22e776ac74c5c259b9c361f6eeea019
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="112---workflowinstancesuspendedrecord"></a><span data-ttu-id="e880d-102">112 - WorkflowInstanceSuspendedRecord</span><span class="sxs-lookup"><span data-stu-id="e880d-102">112 - WorkflowInstanceSuspendedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="e880d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e880d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e880d-104">ID</span><span class="sxs-lookup"><span data-stu-id="e880d-104">Id</span></span>|<span data-ttu-id="e880d-105">112</span><span class="sxs-lookup"><span data-stu-id="e880d-105">112</span></span>|  
|<span data-ttu-id="e880d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e880d-106">Keywords</span></span>|<span data-ttu-id="e880d-107">EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="e880d-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="e880d-108">層級</span><span class="sxs-lookup"><span data-stu-id="e880d-108">Level</span></span>|<span data-ttu-id="e880d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e880d-109">Information</span></span>|  
|<span data-ttu-id="e880d-110">通道</span><span class="sxs-lookup"><span data-stu-id="e880d-110">Channel</span></span>|<span data-ttu-id="e880d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e880d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e880d-112">描述</span><span class="sxs-lookup"><span data-stu-id="e880d-112">Description</span></span>  
 <span data-ttu-id="e880d-113">此事件是當工作流程執行個體發出 WorkflowInstanceSuspended Record 時，由 ETW 追蹤參與者發出。</span><span class="sxs-lookup"><span data-stu-id="e880d-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e880d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e880d-114">Message</span></span>  
 <span data-ttu-id="e880d-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="e880d-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="e880d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e880d-116">Details</span></span>  
  
|<span data-ttu-id="e880d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e880d-117">Data Item Name</span></span>|<span data-ttu-id="e880d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e880d-118">Data Item Type</span></span>|<span data-ttu-id="e880d-119">描述</span><span class="sxs-lookup"><span data-stu-id="e880d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e880d-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e880d-120">InstanceId</span></span>|<span data-ttu-id="e880d-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="e880d-121">xs:GUID</span></span>|<span data-ttu-id="e880d-122">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="e880d-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e880d-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="e880d-123">RecordNumber</span></span>|<span data-ttu-id="e880d-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="e880d-124">xs:long</span></span>|<span data-ttu-id="e880d-125">發出之記錄的序號。</span><span class="sxs-lookup"><span data-stu-id="e880d-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="e880d-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="e880d-126">EventTime</span></span>|<span data-ttu-id="e880d-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="e880d-127">xs:dateTime</span></span>|<span data-ttu-id="e880d-128">發出事件時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="e880d-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="e880d-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="e880d-129">ActivityDefinitionId</span></span>|<span data-ttu-id="e880d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e880d-130">xs:string</span></span>|<span data-ttu-id="e880d-131">工作流程中根活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="e880d-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="e880d-132">原因</span><span class="sxs-lookup"><span data-stu-id="e880d-132">Reason</span></span>|<span data-ttu-id="e880d-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="e880d-133">xs:string</span></span>|<span data-ttu-id="e880d-134">工作流程暫止的原因。</span><span class="sxs-lookup"><span data-stu-id="e880d-134">The reason the workflow was suspended</span></span>|  
|<span data-ttu-id="e880d-135">標註</span><span class="sxs-lookup"><span data-stu-id="e880d-135">Annotations</span></span>|<span data-ttu-id="e880d-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="e880d-136">xs:string</span></span>|<span data-ttu-id="e880d-137">加入至此事件中的附註。</span><span class="sxs-lookup"><span data-stu-id="e880d-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="e880d-138">值會儲存在 xml 中的項目格式\<項目 >\<項目名稱 ="annotationName"type ="> annotationValue\</項目 > \< /i >。</span><span class="sxs-lookup"><span data-stu-id="e880d-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="e880d-139">如果沒有指定的註釋的字串，包含\<項目 / >。</span><span class="sxs-lookup"><span data-stu-id="e880d-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="e880d-140">ETW 事件大小會受到 ETW 緩衝區大小或 ETW 事件的最大承載所限制。</span><span class="sxs-lookup"><span data-stu-id="e880d-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="e880d-141">如果事件大小超過 ETW 限制，則事件會捨棄註釋，並取代具有註釋值截斷\<項目 >... \< /i >。</span><span class="sxs-lookup"><span data-stu-id="e880d-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="e880d-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="e880d-142">ProfileName</span></span>|<span data-ttu-id="e880d-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e880d-143">xs:string</span></span>|<span data-ttu-id="e880d-144">造成發送這個事件的名稱或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="e880d-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="e880d-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="e880d-145">HostReference</span></span>|<span data-ttu-id="e880d-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="e880d-146">xs:string</span></span>|<span data-ttu-id="e880d-147">若為 Web 主控服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="e880d-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="e880d-148">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName' 範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="e880d-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="e880d-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e880d-149">AppDomain</span></span>|<span data-ttu-id="e880d-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="e880d-150">xs:string</span></span>|<span data-ttu-id="e880d-151">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e880d-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
