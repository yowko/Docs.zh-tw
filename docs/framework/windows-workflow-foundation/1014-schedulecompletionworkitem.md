---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982263"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="5a8a3-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="5a8a3-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5a8a3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5a8a3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a8a3-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="5a8a3-104">ID</span></span>|<span data-ttu-id="5a8a3-105">1014</span><span class="sxs-lookup"><span data-stu-id="5a8a3-105">1014</span></span>|  
|<span data-ttu-id="5a8a3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5a8a3-106">Keywords</span></span>|<span data-ttu-id="5a8a3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5a8a3-107">WFRuntime</span></span>|  
|<span data-ttu-id="5a8a3-108">層級</span><span class="sxs-lookup"><span data-stu-id="5a8a3-108">Level</span></span>|<span data-ttu-id="5a8a3-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5a8a3-109">Verbose</span></span>|  
|<span data-ttu-id="5a8a3-110">通道</span><span class="sxs-lookup"><span data-stu-id="5a8a3-110">Channel</span></span>|<span data-ttu-id="5a8a3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5a8a3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5a8a3-112">描述</span><span class="sxs-lookup"><span data-stu-id="5a8a3-112">Description</span></span>  
 <span data-ttu-id="5a8a3-113">表示已排定 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5a8a3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5a8a3-114">Message</span></span>  
 <span data-ttu-id="5a8a3-115">已排定 CompletionWorkItem 父活動 '%1'，DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5a8a3-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5a8a3-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5a8a3-117">Details</span></span>  
  
|<span data-ttu-id="5a8a3-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5a8a3-118">Data Item Name</span></span>|<span data-ttu-id="5a8a3-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5a8a3-119">Data Item Type</span></span>|<span data-ttu-id="5a8a3-120">描述</span><span class="sxs-lookup"><span data-stu-id="5a8a3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5a8a3-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="5a8a3-121">ParentActivity</span></span>|<span data-ttu-id="5a8a3-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-122">xs:string</span></span>|<span data-ttu-id="5a8a3-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="5a8a3-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="5a8a3-124">ParentDisplayName</span></span>|<span data-ttu-id="5a8a3-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-125">xs:string</span></span>|<span data-ttu-id="5a8a3-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="5a8a3-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="5a8a3-127">ParentInstanceId</span></span>|<span data-ttu-id="5a8a3-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-128">xs:string</span></span>|<span data-ttu-id="5a8a3-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="5a8a3-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="5a8a3-130">CompletedActivity</span></span>|<span data-ttu-id="5a8a3-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-131">xs:string</span></span>|<span data-ttu-id="5a8a3-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="5a8a3-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="5a8a3-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="5a8a3-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-134">xs:string</span></span>|<span data-ttu-id="5a8a3-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="5a8a3-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="5a8a3-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="5a8a3-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-137">xs:string</span></span>|<span data-ttu-id="5a8a3-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="5a8a3-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5a8a3-139">AppDomain</span></span>|<span data-ttu-id="5a8a3-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="5a8a3-140">xs:string</span></span>|<span data-ttu-id="5a8a3-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5a8a3-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
