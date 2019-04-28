---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925082"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="1f9da-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="1f9da-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1f9da-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1f9da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1f9da-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="1f9da-104">ID</span></span>|<span data-ttu-id="1f9da-105">1016</span><span class="sxs-lookup"><span data-stu-id="1f9da-105">1016</span></span>|  
|<span data-ttu-id="1f9da-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f9da-106">Keywords</span></span>|<span data-ttu-id="1f9da-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1f9da-107">WFRuntime</span></span>|  
|<span data-ttu-id="1f9da-108">層級</span><span class="sxs-lookup"><span data-stu-id="1f9da-108">Level</span></span>|<span data-ttu-id="1f9da-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="1f9da-109">Verbose</span></span>|  
|<span data-ttu-id="1f9da-110">通道</span><span class="sxs-lookup"><span data-stu-id="1f9da-110">Channel</span></span>|<span data-ttu-id="1f9da-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1f9da-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1f9da-112">描述</span><span class="sxs-lookup"><span data-stu-id="1f9da-112">Description</span></span>  
 <span data-ttu-id="1f9da-113">表示 CompletionWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="1f9da-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1f9da-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1f9da-114">Message</span></span>  
 <span data-ttu-id="1f9da-115">已完成父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="1f9da-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1f9da-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="1f9da-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1f9da-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1f9da-117">Details</span></span>  
  
|<span data-ttu-id="1f9da-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1f9da-118">Data Item Name</span></span>|<span data-ttu-id="1f9da-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1f9da-119">Data Item Type</span></span>|<span data-ttu-id="1f9da-120">描述</span><span class="sxs-lookup"><span data-stu-id="1f9da-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1f9da-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="1f9da-121">ParentActivity</span></span>|<span data-ttu-id="1f9da-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-122">xs:string</span></span>|<span data-ttu-id="1f9da-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f9da-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1f9da-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="1f9da-124">ParentDisplayName</span></span>|<span data-ttu-id="1f9da-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-125">xs:string</span></span>|<span data-ttu-id="1f9da-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1f9da-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1f9da-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1f9da-127">ParentInstanceId</span></span>|<span data-ttu-id="1f9da-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-128">xs:string</span></span>|<span data-ttu-id="1f9da-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1f9da-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1f9da-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="1f9da-130">CompletedActivity</span></span>|<span data-ttu-id="1f9da-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-131">xs:string</span></span>|<span data-ttu-id="1f9da-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1f9da-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="1f9da-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1f9da-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="1f9da-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-134">xs:string</span></span>|<span data-ttu-id="1f9da-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1f9da-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="1f9da-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1f9da-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="1f9da-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-137">xs:string</span></span>|<span data-ttu-id="1f9da-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1f9da-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="1f9da-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1f9da-139">AppDomain</span></span>|<span data-ttu-id="1f9da-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="1f9da-140">xs:string</span></span>|<span data-ttu-id="1f9da-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1f9da-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
