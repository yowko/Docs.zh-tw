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
ms.openlocfilehash: 3d483a681cae6328dd6111b320a12b5a064d3ff5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="d5aa8-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="d5aa8-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d5aa8-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d5aa8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5aa8-104">ID</span><span class="sxs-lookup"><span data-stu-id="d5aa8-104">ID</span></span>|<span data-ttu-id="d5aa8-105">1014</span><span class="sxs-lookup"><span data-stu-id="d5aa8-105">1014</span></span>|  
|<span data-ttu-id="d5aa8-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d5aa8-106">Keywords</span></span>|<span data-ttu-id="d5aa8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d5aa8-107">WFRuntime</span></span>|  
|<span data-ttu-id="d5aa8-108">層級</span><span class="sxs-lookup"><span data-stu-id="d5aa8-108">Level</span></span>|<span data-ttu-id="d5aa8-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d5aa8-109">Verbose</span></span>|  
|<span data-ttu-id="d5aa8-110">通道</span><span class="sxs-lookup"><span data-stu-id="d5aa8-110">Channel</span></span>|<span data-ttu-id="d5aa8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d5aa8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d5aa8-112">描述</span><span class="sxs-lookup"><span data-stu-id="d5aa8-112">Description</span></span>  
 <span data-ttu-id="d5aa8-113">表示已排定 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d5aa8-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d5aa8-114">Message</span></span>  
 <span data-ttu-id="d5aa8-115">已排定 CompletionWorkItem 父活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="d5aa8-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d5aa8-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5aa8-117">Details</span></span>  
  
|<span data-ttu-id="d5aa8-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d5aa8-118">Data Item Name</span></span>|<span data-ttu-id="d5aa8-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d5aa8-119">Data Item Type</span></span>|<span data-ttu-id="d5aa8-120">描述</span><span class="sxs-lookup"><span data-stu-id="d5aa8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d5aa8-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="d5aa8-121">ParentActivity</span></span>|<span data-ttu-id="d5aa8-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-122">xs:string</span></span>|<span data-ttu-id="d5aa8-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="d5aa8-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="d5aa8-124">ParentDisplayName</span></span>|<span data-ttu-id="d5aa8-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-125">xs:string</span></span>|<span data-ttu-id="d5aa8-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="d5aa8-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="d5aa8-127">ParentInstanceId</span></span>|<span data-ttu-id="d5aa8-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-128">xs:string</span></span>|<span data-ttu-id="d5aa8-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="d5aa8-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="d5aa8-130">CompletedActivity</span></span>|<span data-ttu-id="d5aa8-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-131">xs:string</span></span>|<span data-ttu-id="d5aa8-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="d5aa8-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d5aa8-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="d5aa8-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-134">xs:string</span></span>|<span data-ttu-id="d5aa8-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="d5aa8-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d5aa8-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="d5aa8-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-137">xs:string</span></span>|<span data-ttu-id="d5aa8-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="d5aa8-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d5aa8-139">AppDomain</span></span>|<span data-ttu-id="d5aa8-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5aa8-140">xs:string</span></span>|<span data-ttu-id="d5aa8-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d5aa8-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
