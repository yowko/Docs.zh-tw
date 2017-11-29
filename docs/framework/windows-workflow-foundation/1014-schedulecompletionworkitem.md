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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="23f4e-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="23f4e-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="23f4e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="23f4e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23f4e-104">ID</span><span class="sxs-lookup"><span data-stu-id="23f4e-104">ID</span></span>|<span data-ttu-id="23f4e-105">1014</span><span class="sxs-lookup"><span data-stu-id="23f4e-105">1014</span></span>|  
|<span data-ttu-id="23f4e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="23f4e-106">Keywords</span></span>|<span data-ttu-id="23f4e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="23f4e-107">WFRuntime</span></span>|  
|<span data-ttu-id="23f4e-108">層級</span><span class="sxs-lookup"><span data-stu-id="23f4e-108">Level</span></span>|<span data-ttu-id="23f4e-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="23f4e-109">Verbose</span></span>|  
|<span data-ttu-id="23f4e-110">通道</span><span class="sxs-lookup"><span data-stu-id="23f4e-110">Channel</span></span>|<span data-ttu-id="23f4e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="23f4e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="23f4e-112">描述</span><span class="sxs-lookup"><span data-stu-id="23f4e-112">Description</span></span>  
 <span data-ttu-id="23f4e-113">表示已排定 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="23f4e-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="23f4e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="23f4e-114">Message</span></span>  
 <span data-ttu-id="23f4e-115">已排定 CompletionWorkItem 父活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="23f4e-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="23f4e-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="23f4e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="23f4e-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23f4e-117">Details</span></span>  
  
|<span data-ttu-id="23f4e-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="23f4e-118">Data Item Name</span></span>|<span data-ttu-id="23f4e-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="23f4e-119">Data Item Type</span></span>|<span data-ttu-id="23f4e-120">描述</span><span class="sxs-lookup"><span data-stu-id="23f4e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="23f4e-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="23f4e-121">ParentActivity</span></span>|<span data-ttu-id="23f4e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-122">xs:string</span></span>|<span data-ttu-id="23f4e-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="23f4e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="23f4e-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="23f4e-124">ParentDisplayName</span></span>|<span data-ttu-id="23f4e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-125">xs:string</span></span>|<span data-ttu-id="23f4e-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="23f4e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="23f4e-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="23f4e-127">ParentInstanceId</span></span>|<span data-ttu-id="23f4e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-128">xs:string</span></span>|<span data-ttu-id="23f4e-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="23f4e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="23f4e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="23f4e-130">CompletedActivity</span></span>|<span data-ttu-id="23f4e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-131">xs:string</span></span>|<span data-ttu-id="23f4e-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="23f4e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="23f4e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="23f4e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="23f4e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-134">xs:string</span></span>|<span data-ttu-id="23f4e-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="23f4e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="23f4e-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="23f4e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="23f4e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-137">xs:string</span></span>|<span data-ttu-id="23f4e-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="23f4e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="23f4e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="23f4e-139">AppDomain</span></span>|<span data-ttu-id="23f4e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="23f4e-140">xs:string</span></span>|<span data-ttu-id="23f4e-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="23f4e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
