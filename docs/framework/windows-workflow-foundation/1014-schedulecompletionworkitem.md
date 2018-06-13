---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510363"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="b1a67-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="b1a67-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b1a67-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b1a67-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1a67-104">ID</span><span class="sxs-lookup"><span data-stu-id="b1a67-104">ID</span></span>|<span data-ttu-id="b1a67-105">1014</span><span class="sxs-lookup"><span data-stu-id="b1a67-105">1014</span></span>|  
|<span data-ttu-id="b1a67-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b1a67-106">Keywords</span></span>|<span data-ttu-id="b1a67-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b1a67-107">WFRuntime</span></span>|  
|<span data-ttu-id="b1a67-108">層級</span><span class="sxs-lookup"><span data-stu-id="b1a67-108">Level</span></span>|<span data-ttu-id="b1a67-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b1a67-109">Verbose</span></span>|  
|<span data-ttu-id="b1a67-110">通道</span><span class="sxs-lookup"><span data-stu-id="b1a67-110">Channel</span></span>|<span data-ttu-id="b1a67-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b1a67-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b1a67-112">描述</span><span class="sxs-lookup"><span data-stu-id="b1a67-112">Description</span></span>  
 <span data-ttu-id="b1a67-113">表示已排定 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="b1a67-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b1a67-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b1a67-114">Message</span></span>  
 <span data-ttu-id="b1a67-115">已排定 CompletionWorkItem 父活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="b1a67-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="b1a67-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="b1a67-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b1a67-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b1a67-117">Details</span></span>  
  
|<span data-ttu-id="b1a67-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b1a67-118">Data Item Name</span></span>|<span data-ttu-id="b1a67-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b1a67-119">Data Item Type</span></span>|<span data-ttu-id="b1a67-120">描述</span><span class="sxs-lookup"><span data-stu-id="b1a67-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b1a67-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="b1a67-121">ParentActivity</span></span>|<span data-ttu-id="b1a67-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-122">xs:string</span></span>|<span data-ttu-id="b1a67-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b1a67-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="b1a67-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="b1a67-124">ParentDisplayName</span></span>|<span data-ttu-id="b1a67-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-125">xs:string</span></span>|<span data-ttu-id="b1a67-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b1a67-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="b1a67-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="b1a67-127">ParentInstanceId</span></span>|<span data-ttu-id="b1a67-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-128">xs:string</span></span>|<span data-ttu-id="b1a67-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="b1a67-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="b1a67-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="b1a67-130">CompletedActivity</span></span>|<span data-ttu-id="b1a67-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-131">xs:string</span></span>|<span data-ttu-id="b1a67-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b1a67-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="b1a67-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b1a67-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="b1a67-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-134">xs:string</span></span>|<span data-ttu-id="b1a67-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b1a67-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="b1a67-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b1a67-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="b1a67-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-137">xs:string</span></span>|<span data-ttu-id="b1a67-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="b1a67-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="b1a67-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b1a67-139">AppDomain</span></span>|<span data-ttu-id="b1a67-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="b1a67-140">xs:string</span></span>|<span data-ttu-id="b1a67-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b1a67-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
