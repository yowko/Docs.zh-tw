---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a80406ce56000703555f7834714222e03d2b65f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="147ae-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="147ae-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="147ae-103">屬性</span><span class="sxs-lookup"><span data-stu-id="147ae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="147ae-104">ID</span><span class="sxs-lookup"><span data-stu-id="147ae-104">ID</span></span>|<span data-ttu-id="147ae-105">1014</span><span class="sxs-lookup"><span data-stu-id="147ae-105">1014</span></span>|  
|<span data-ttu-id="147ae-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="147ae-106">Keywords</span></span>|<span data-ttu-id="147ae-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="147ae-107">WFRuntime</span></span>|  
|<span data-ttu-id="147ae-108">層級</span><span class="sxs-lookup"><span data-stu-id="147ae-108">Level</span></span>|<span data-ttu-id="147ae-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="147ae-109">Verbose</span></span>|  
|<span data-ttu-id="147ae-110">通道</span><span class="sxs-lookup"><span data-stu-id="147ae-110">Channel</span></span>|<span data-ttu-id="147ae-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="147ae-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="147ae-112">描述</span><span class="sxs-lookup"><span data-stu-id="147ae-112">Description</span></span>  
 <span data-ttu-id="147ae-113">表示已排定 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="147ae-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="147ae-114">訊息</span><span class="sxs-lookup"><span data-stu-id="147ae-114">Message</span></span>  
 <span data-ttu-id="147ae-115">已排定 CompletionWorkItem 父活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="147ae-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="147ae-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="147ae-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="147ae-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="147ae-117">Details</span></span>  
  
|<span data-ttu-id="147ae-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="147ae-118">Data Item Name</span></span>|<span data-ttu-id="147ae-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="147ae-119">Data Item Type</span></span>|<span data-ttu-id="147ae-120">描述</span><span class="sxs-lookup"><span data-stu-id="147ae-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="147ae-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="147ae-121">ParentActivity</span></span>|<span data-ttu-id="147ae-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-122">xs:string</span></span>|<span data-ttu-id="147ae-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="147ae-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="147ae-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="147ae-124">ParentDisplayName</span></span>|<span data-ttu-id="147ae-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-125">xs:string</span></span>|<span data-ttu-id="147ae-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="147ae-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="147ae-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="147ae-127">ParentInstanceId</span></span>|<span data-ttu-id="147ae-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-128">xs:string</span></span>|<span data-ttu-id="147ae-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="147ae-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="147ae-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="147ae-130">CompletedActivity</span></span>|<span data-ttu-id="147ae-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-131">xs:string</span></span>|<span data-ttu-id="147ae-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="147ae-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="147ae-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="147ae-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="147ae-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-134">xs:string</span></span>|<span data-ttu-id="147ae-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="147ae-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="147ae-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="147ae-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="147ae-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-137">xs:string</span></span>|<span data-ttu-id="147ae-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="147ae-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="147ae-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="147ae-139">AppDomain</span></span>|<span data-ttu-id="147ae-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="147ae-140">xs:string</span></span>|<span data-ttu-id="147ae-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="147ae-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
