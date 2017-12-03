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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b01706f6e84987ea20f52c131139e243e8184c51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="9ac16-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="9ac16-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9ac16-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9ac16-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ac16-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ac16-104">ID</span></span>|<span data-ttu-id="9ac16-105">1016</span><span class="sxs-lookup"><span data-stu-id="9ac16-105">1016</span></span>|  
|<span data-ttu-id="9ac16-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9ac16-106">Keywords</span></span>|<span data-ttu-id="9ac16-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9ac16-107">WFRuntime</span></span>|  
|<span data-ttu-id="9ac16-108">層級</span><span class="sxs-lookup"><span data-stu-id="9ac16-108">Level</span></span>|<span data-ttu-id="9ac16-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9ac16-109">Verbose</span></span>|  
|<span data-ttu-id="9ac16-110">通道</span><span class="sxs-lookup"><span data-stu-id="9ac16-110">Channel</span></span>|<span data-ttu-id="9ac16-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9ac16-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ac16-112">描述</span><span class="sxs-lookup"><span data-stu-id="9ac16-112">Description</span></span>  
 <span data-ttu-id="9ac16-113">表示 CompletionWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="9ac16-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ac16-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9ac16-114">Message</span></span>  
 <span data-ttu-id="9ac16-115">已完成父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="9ac16-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="9ac16-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="9ac16-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ac16-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9ac16-117">Details</span></span>  
  
|<span data-ttu-id="9ac16-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9ac16-118">Data Item Name</span></span>|<span data-ttu-id="9ac16-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9ac16-119">Data Item Type</span></span>|<span data-ttu-id="9ac16-120">描述</span><span class="sxs-lookup"><span data-stu-id="9ac16-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ac16-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="9ac16-121">ParentActivity</span></span>|<span data-ttu-id="9ac16-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-122">xs:string</span></span>|<span data-ttu-id="9ac16-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9ac16-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="9ac16-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="9ac16-124">ParentDisplayName</span></span>|<span data-ttu-id="9ac16-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-125">xs:string</span></span>|<span data-ttu-id="9ac16-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9ac16-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="9ac16-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="9ac16-127">ParentInstanceId</span></span>|<span data-ttu-id="9ac16-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-128">xs:string</span></span>|<span data-ttu-id="9ac16-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9ac16-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="9ac16-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="9ac16-130">CompletedActivity</span></span>|<span data-ttu-id="9ac16-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-131">xs:string</span></span>|<span data-ttu-id="9ac16-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9ac16-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="9ac16-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9ac16-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="9ac16-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-134">xs:string</span></span>|<span data-ttu-id="9ac16-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9ac16-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="9ac16-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9ac16-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="9ac16-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-137">xs:string</span></span>|<span data-ttu-id="9ac16-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9ac16-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="9ac16-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ac16-139">AppDomain</span></span>|<span data-ttu-id="9ac16-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ac16-140">xs:string</span></span>|<span data-ttu-id="9ac16-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9ac16-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
