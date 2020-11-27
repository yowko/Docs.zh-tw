---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: a192ffe19777ca3e2e9784f6506a0c2929ced000
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275527"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="70e2d-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="70e2d-102">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="70e2d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="70e2d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70e2d-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="70e2d-104">ID</span></span>|<span data-ttu-id="70e2d-105">1016</span><span class="sxs-lookup"><span data-stu-id="70e2d-105">1016</span></span>|  
|<span data-ttu-id="70e2d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="70e2d-106">Keywords</span></span>|<span data-ttu-id="70e2d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="70e2d-107">WFRuntime</span></span>|  
|<span data-ttu-id="70e2d-108">層級</span><span class="sxs-lookup"><span data-stu-id="70e2d-108">Level</span></span>|<span data-ttu-id="70e2d-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="70e2d-109">Verbose</span></span>|  
|<span data-ttu-id="70e2d-110">通路</span><span class="sxs-lookup"><span data-stu-id="70e2d-110">Channel</span></span>|<span data-ttu-id="70e2d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="70e2d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="70e2d-112">描述</span><span class="sxs-lookup"><span data-stu-id="70e2d-112">Description</span></span>  

 <span data-ttu-id="70e2d-113">表示 CompletionWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="70e2d-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="70e2d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="70e2d-114">Message</span></span>  

 <span data-ttu-id="70e2d-115">已完成父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="70e2d-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="70e2d-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="70e2d-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="70e2d-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="70e2d-117">Details</span></span>  
  
|<span data-ttu-id="70e2d-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="70e2d-118">Data Item Name</span></span>|<span data-ttu-id="70e2d-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="70e2d-119">Data Item Type</span></span>|<span data-ttu-id="70e2d-120">描述</span><span class="sxs-lookup"><span data-stu-id="70e2d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="70e2d-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="70e2d-121">ParentActivity</span></span>|<span data-ttu-id="70e2d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-122">xs:string</span></span>|<span data-ttu-id="70e2d-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="70e2d-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="70e2d-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="70e2d-124">ParentDisplayName</span></span>|<span data-ttu-id="70e2d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-125">xs:string</span></span>|<span data-ttu-id="70e2d-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="70e2d-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="70e2d-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="70e2d-127">ParentInstanceId</span></span>|<span data-ttu-id="70e2d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-128">xs:string</span></span>|<span data-ttu-id="70e2d-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="70e2d-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="70e2d-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="70e2d-130">CompletedActivity</span></span>|<span data-ttu-id="70e2d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-131">xs:string</span></span>|<span data-ttu-id="70e2d-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="70e2d-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="70e2d-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="70e2d-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="70e2d-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-134">xs:string</span></span>|<span data-ttu-id="70e2d-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="70e2d-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="70e2d-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="70e2d-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="70e2d-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-137">xs:string</span></span>|<span data-ttu-id="70e2d-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="70e2d-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="70e2d-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="70e2d-139">AppDomain</span></span>|<span data-ttu-id="70e2d-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="70e2d-140">xs:string</span></span>|<span data-ttu-id="70e2d-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="70e2d-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
