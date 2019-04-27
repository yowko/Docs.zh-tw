---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924653"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="14f5c-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="14f5c-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="14f5c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="14f5c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14f5c-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="14f5c-104">ID</span></span>|<span data-ttu-id="14f5c-105">1009</span><span class="sxs-lookup"><span data-stu-id="14f5c-105">1009</span></span>|  
|<span data-ttu-id="14f5c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="14f5c-106">Keywords</span></span>|<span data-ttu-id="14f5c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="14f5c-107">WFRuntime</span></span>|  
|<span data-ttu-id="14f5c-108">層級</span><span class="sxs-lookup"><span data-stu-id="14f5c-108">Level</span></span>|<span data-ttu-id="14f5c-109">資訊</span><span class="sxs-lookup"><span data-stu-id="14f5c-109">Information</span></span>|  
|<span data-ttu-id="14f5c-110">通道</span><span class="sxs-lookup"><span data-stu-id="14f5c-110">Channel</span></span>|<span data-ttu-id="14f5c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="14f5c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14f5c-112">描述</span><span class="sxs-lookup"><span data-stu-id="14f5c-112">Description</span></span>  
 <span data-ttu-id="14f5c-113">表示活動正在排定執行。</span><span class="sxs-lookup"><span data-stu-id="14f5c-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14f5c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="14f5c-114">Message</span></span>  
 <span data-ttu-id="14f5c-115">父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程子活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="14f5c-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14f5c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14f5c-116">Details</span></span>  
  
|<span data-ttu-id="14f5c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="14f5c-117">Data Item Name</span></span>|<span data-ttu-id="14f5c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="14f5c-118">Data Item Type</span></span>|<span data-ttu-id="14f5c-119">描述</span><span class="sxs-lookup"><span data-stu-id="14f5c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14f5c-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="14f5c-120">ParentActivity</span></span>|<span data-ttu-id="14f5c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-121">xs:string</span></span>|<span data-ttu-id="14f5c-122">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="14f5c-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="14f5c-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="14f5c-123">ParentDisplayName</span></span>|<span data-ttu-id="14f5c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-124">xs:string</span></span>|<span data-ttu-id="14f5c-125">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="14f5c-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="14f5c-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="14f5c-126">ParentInstanceId</span></span>|<span data-ttu-id="14f5c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-127">xs:string</span></span>|<span data-ttu-id="14f5c-128">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="14f5c-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="14f5c-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="14f5c-129">ChildActivity</span></span>|<span data-ttu-id="14f5c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-130">xs:string</span></span>|<span data-ttu-id="14f5c-131">已排程之子活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="14f5c-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="14f5c-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="14f5c-132">ChildDisplayName</span></span>|<span data-ttu-id="14f5c-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-133">xs:string</span></span>|<span data-ttu-id="14f5c-134">已排程之子活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="14f5c-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="14f5c-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="14f5c-135">ChildInstanceId</span></span>|<span data-ttu-id="14f5c-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-136">xs:string</span></span>|<span data-ttu-id="14f5c-137">已排程之子活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="14f5c-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="14f5c-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14f5c-138">AppDomain</span></span>|<span data-ttu-id="14f5c-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="14f5c-139">xs:string</span></span>|<span data-ttu-id="14f5c-140">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="14f5c-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
