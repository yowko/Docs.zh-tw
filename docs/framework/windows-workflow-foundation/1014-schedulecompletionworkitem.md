---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 7fd93683851c5a8c4ab253272c3f2129b3f0bb49
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275553"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="68f1e-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="68f1e-102">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="68f1e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="68f1e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68f1e-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="68f1e-104">ID</span></span>|<span data-ttu-id="68f1e-105">1014</span><span class="sxs-lookup"><span data-stu-id="68f1e-105">1014</span></span>|  
|<span data-ttu-id="68f1e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="68f1e-106">Keywords</span></span>|<span data-ttu-id="68f1e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="68f1e-107">WFRuntime</span></span>|  
|<span data-ttu-id="68f1e-108">層級</span><span class="sxs-lookup"><span data-stu-id="68f1e-108">Level</span></span>|<span data-ttu-id="68f1e-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="68f1e-109">Verbose</span></span>|  
|<span data-ttu-id="68f1e-110">通路</span><span class="sxs-lookup"><span data-stu-id="68f1e-110">Channel</span></span>|<span data-ttu-id="68f1e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="68f1e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68f1e-112">描述</span><span class="sxs-lookup"><span data-stu-id="68f1e-112">Description</span></span>  

 <span data-ttu-id="68f1e-113">表示已排定 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="68f1e-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68f1e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="68f1e-114">Message</span></span>  

 <span data-ttu-id="68f1e-115">已排程父活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="68f1e-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="68f1e-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="68f1e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68f1e-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="68f1e-117">Details</span></span>  
  
|<span data-ttu-id="68f1e-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="68f1e-118">Data Item Name</span></span>|<span data-ttu-id="68f1e-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="68f1e-119">Data Item Type</span></span>|<span data-ttu-id="68f1e-120">描述</span><span class="sxs-lookup"><span data-stu-id="68f1e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68f1e-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="68f1e-121">ParentActivity</span></span>|<span data-ttu-id="68f1e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-122">xs:string</span></span>|<span data-ttu-id="68f1e-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="68f1e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="68f1e-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="68f1e-124">ParentDisplayName</span></span>|<span data-ttu-id="68f1e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-125">xs:string</span></span>|<span data-ttu-id="68f1e-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="68f1e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="68f1e-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="68f1e-127">ParentInstanceId</span></span>|<span data-ttu-id="68f1e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-128">xs:string</span></span>|<span data-ttu-id="68f1e-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="68f1e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="68f1e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="68f1e-130">CompletedActivity</span></span>|<span data-ttu-id="68f1e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-131">xs:string</span></span>|<span data-ttu-id="68f1e-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="68f1e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="68f1e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="68f1e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="68f1e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-134">xs:string</span></span>|<span data-ttu-id="68f1e-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="68f1e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="68f1e-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="68f1e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="68f1e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-137">xs:string</span></span>|<span data-ttu-id="68f1e-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="68f1e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="68f1e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68f1e-139">AppDomain</span></span>|<span data-ttu-id="68f1e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="68f1e-140">xs:string</span></span>|<span data-ttu-id="68f1e-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="68f1e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
