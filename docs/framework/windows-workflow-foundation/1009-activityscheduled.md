---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdaa8ca4efeffb3895e0056303721b13cdc1ae27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="7b4b5-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="7b4b5-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="7b4b5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="7b4b5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b4b5-104">ID</span><span class="sxs-lookup"><span data-stu-id="7b4b5-104">ID</span></span>|<span data-ttu-id="7b4b5-105">1009</span><span class="sxs-lookup"><span data-stu-id="7b4b5-105">1009</span></span>|  
|<span data-ttu-id="7b4b5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7b4b5-106">Keywords</span></span>|<span data-ttu-id="7b4b5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7b4b5-107">WFRuntime</span></span>|  
|<span data-ttu-id="7b4b5-108">層級</span><span class="sxs-lookup"><span data-stu-id="7b4b5-108">Level</span></span>|<span data-ttu-id="7b4b5-109">資訊</span><span class="sxs-lookup"><span data-stu-id="7b4b5-109">Information</span></span>|  
|<span data-ttu-id="7b4b5-110">通道</span><span class="sxs-lookup"><span data-stu-id="7b4b5-110">Channel</span></span>|<span data-ttu-id="7b4b5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7b4b5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7b4b5-112">描述</span><span class="sxs-lookup"><span data-stu-id="7b4b5-112">Description</span></span>  
 <span data-ttu-id="7b4b5-113">表示活動正在排定執行。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7b4b5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="7b4b5-114">Message</span></span>  
 <span data-ttu-id="7b4b5-115">父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程子活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7b4b5-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b4b5-116">Details</span></span>  
  
|<span data-ttu-id="7b4b5-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="7b4b5-117">Data Item Name</span></span>|<span data-ttu-id="7b4b5-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="7b4b5-118">Data Item Type</span></span>|<span data-ttu-id="7b4b5-119">描述</span><span class="sxs-lookup"><span data-stu-id="7b4b5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7b4b5-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="7b4b5-120">ParentActivity</span></span>|<span data-ttu-id="7b4b5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-121">xs:string</span></span>|<span data-ttu-id="7b4b5-122">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="7b4b5-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="7b4b5-123">ParentDisplayName</span></span>|<span data-ttu-id="7b4b5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-124">xs:string</span></span>|<span data-ttu-id="7b4b5-125">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="7b4b5-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="7b4b5-126">ParentInstanceId</span></span>|<span data-ttu-id="7b4b5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-127">xs:string</span></span>|<span data-ttu-id="7b4b5-128">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="7b4b5-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="7b4b5-129">ChildActivity</span></span>|<span data-ttu-id="7b4b5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-130">xs:string</span></span>|<span data-ttu-id="7b4b5-131">已排程之子活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="7b4b5-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="7b4b5-132">ChildDisplayName</span></span>|<span data-ttu-id="7b4b5-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-133">xs:string</span></span>|<span data-ttu-id="7b4b5-134">已排程之子活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="7b4b5-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="7b4b5-135">ChildInstanceId</span></span>|<span data-ttu-id="7b4b5-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-136">xs:string</span></span>|<span data-ttu-id="7b4b5-137">已排程之子活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="7b4b5-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7b4b5-138">AppDomain</span></span>|<span data-ttu-id="7b4b5-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="7b4b5-139">xs:string</span></span>|<span data-ttu-id="7b4b5-140">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7b4b5-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
