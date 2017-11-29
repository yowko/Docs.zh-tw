---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a7c6b6060e8dd3256d23db7350299d2670f6caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="58e2f-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="58e2f-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="58e2f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="58e2f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58e2f-104">ID</span><span class="sxs-lookup"><span data-stu-id="58e2f-104">ID</span></span>|<span data-ttu-id="58e2f-105">1016</span><span class="sxs-lookup"><span data-stu-id="58e2f-105">1016</span></span>|  
|<span data-ttu-id="58e2f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="58e2f-106">Keywords</span></span>|<span data-ttu-id="58e2f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="58e2f-107">WFRuntime</span></span>|  
|<span data-ttu-id="58e2f-108">層級</span><span class="sxs-lookup"><span data-stu-id="58e2f-108">Level</span></span>|<span data-ttu-id="58e2f-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="58e2f-109">Verbose</span></span>|  
|<span data-ttu-id="58e2f-110">通道</span><span class="sxs-lookup"><span data-stu-id="58e2f-110">Channel</span></span>|<span data-ttu-id="58e2f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="58e2f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58e2f-112">描述</span><span class="sxs-lookup"><span data-stu-id="58e2f-112">Description</span></span>  
 <span data-ttu-id="58e2f-113">表示 CompletionWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="58e2f-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58e2f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="58e2f-114">Message</span></span>  
 <span data-ttu-id="58e2f-115">已完成父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="58e2f-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="58e2f-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="58e2f-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58e2f-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58e2f-117">Details</span></span>  
  
|<span data-ttu-id="58e2f-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="58e2f-118">Data Item Name</span></span>|<span data-ttu-id="58e2f-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="58e2f-119">Data Item Type</span></span>|<span data-ttu-id="58e2f-120">描述</span><span class="sxs-lookup"><span data-stu-id="58e2f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58e2f-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="58e2f-121">ParentActivity</span></span>|<span data-ttu-id="58e2f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-122">xs:string</span></span>|<span data-ttu-id="58e2f-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="58e2f-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="58e2f-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="58e2f-124">ParentDisplayName</span></span>|<span data-ttu-id="58e2f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-125">xs:string</span></span>|<span data-ttu-id="58e2f-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="58e2f-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="58e2f-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="58e2f-127">ParentInstanceId</span></span>|<span data-ttu-id="58e2f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-128">xs:string</span></span>|<span data-ttu-id="58e2f-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="58e2f-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="58e2f-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="58e2f-130">CompletedActivity</span></span>|<span data-ttu-id="58e2f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-131">xs:string</span></span>|<span data-ttu-id="58e2f-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="58e2f-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="58e2f-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="58e2f-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="58e2f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-134">xs:string</span></span>|<span data-ttu-id="58e2f-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="58e2f-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="58e2f-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="58e2f-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="58e2f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-137">xs:string</span></span>|<span data-ttu-id="58e2f-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="58e2f-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="58e2f-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="58e2f-139">AppDomain</span></span>|<span data-ttu-id="58e2f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="58e2f-140">xs:string</span></span>|<span data-ttu-id="58e2f-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="58e2f-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
