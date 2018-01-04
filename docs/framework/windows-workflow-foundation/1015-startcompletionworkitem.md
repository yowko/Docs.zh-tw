---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="1521f-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="1521f-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1521f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1521f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1521f-104">ID</span><span class="sxs-lookup"><span data-stu-id="1521f-104">ID</span></span>|<span data-ttu-id="1521f-105">1015</span><span class="sxs-lookup"><span data-stu-id="1521f-105">1015</span></span>|  
|<span data-ttu-id="1521f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1521f-106">Keywords</span></span>|<span data-ttu-id="1521f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1521f-107">WFRuntime</span></span>|  
|<span data-ttu-id="1521f-108">層級</span><span class="sxs-lookup"><span data-stu-id="1521f-108">Level</span></span>|<span data-ttu-id="1521f-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="1521f-109">Verbose</span></span>|  
|<span data-ttu-id="1521f-110">通道</span><span class="sxs-lookup"><span data-stu-id="1521f-110">Channel</span></span>|<span data-ttu-id="1521f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1521f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1521f-112">描述</span><span class="sxs-lookup"><span data-stu-id="1521f-112">Description</span></span>  
 <span data-ttu-id="1521f-113">表示 CompletionWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="1521f-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1521f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1521f-114">Message</span></span>  
 <span data-ttu-id="1521f-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="1521f-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1521f-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="1521f-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1521f-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1521f-117">Details</span></span>  
  
|<span data-ttu-id="1521f-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1521f-118">Data Item Name</span></span>|<span data-ttu-id="1521f-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1521f-119">Data Item Type</span></span>|<span data-ttu-id="1521f-120">描述</span><span class="sxs-lookup"><span data-stu-id="1521f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1521f-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="1521f-121">ParentActivity</span></span>|<span data-ttu-id="1521f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-122">xs:string</span></span>|<span data-ttu-id="1521f-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1521f-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1521f-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="1521f-124">ParentDisplayName</span></span>|<span data-ttu-id="1521f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-125">xs:string</span></span>|<span data-ttu-id="1521f-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1521f-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1521f-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1521f-127">ParentInstanceId</span></span>|<span data-ttu-id="1521f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-128">xs:string</span></span>|<span data-ttu-id="1521f-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1521f-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1521f-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="1521f-130">CompletedActivity</span></span>|<span data-ttu-id="1521f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-131">xs:string</span></span>|<span data-ttu-id="1521f-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1521f-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="1521f-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1521f-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="1521f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-134">xs:string</span></span>|<span data-ttu-id="1521f-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1521f-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="1521f-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1521f-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="1521f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-137">xs:string</span></span>|<span data-ttu-id="1521f-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1521f-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="1521f-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1521f-139">AppDomain</span></span>|<span data-ttu-id="1521f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="1521f-140">xs:string</span></span>|<span data-ttu-id="1521f-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1521f-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
