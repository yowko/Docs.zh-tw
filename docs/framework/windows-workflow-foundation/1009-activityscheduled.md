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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9463fbf2e7f2ac3424488dc3fca322a91d11126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="1db2d-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="1db2d-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="1db2d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1db2d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1db2d-104">ID</span><span class="sxs-lookup"><span data-stu-id="1db2d-104">ID</span></span>|<span data-ttu-id="1db2d-105">1009</span><span class="sxs-lookup"><span data-stu-id="1db2d-105">1009</span></span>|  
|<span data-ttu-id="1db2d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1db2d-106">Keywords</span></span>|<span data-ttu-id="1db2d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1db2d-107">WFRuntime</span></span>|  
|<span data-ttu-id="1db2d-108">層級</span><span class="sxs-lookup"><span data-stu-id="1db2d-108">Level</span></span>|<span data-ttu-id="1db2d-109">資訊</span><span class="sxs-lookup"><span data-stu-id="1db2d-109">Information</span></span>|  
|<span data-ttu-id="1db2d-110">通道</span><span class="sxs-lookup"><span data-stu-id="1db2d-110">Channel</span></span>|<span data-ttu-id="1db2d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1db2d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1db2d-112">描述</span><span class="sxs-lookup"><span data-stu-id="1db2d-112">Description</span></span>  
 <span data-ttu-id="1db2d-113">表示活動正在排定執行。</span><span class="sxs-lookup"><span data-stu-id="1db2d-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1db2d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1db2d-114">Message</span></span>  
 <span data-ttu-id="1db2d-115">父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程子活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="1db2d-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1db2d-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1db2d-116">Details</span></span>  
  
|<span data-ttu-id="1db2d-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1db2d-117">Data Item Name</span></span>|<span data-ttu-id="1db2d-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1db2d-118">Data Item Type</span></span>|<span data-ttu-id="1db2d-119">描述</span><span class="sxs-lookup"><span data-stu-id="1db2d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1db2d-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="1db2d-120">ParentActivity</span></span>|<span data-ttu-id="1db2d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-121">xs:string</span></span>|<span data-ttu-id="1db2d-122">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1db2d-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1db2d-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="1db2d-123">ParentDisplayName</span></span>|<span data-ttu-id="1db2d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-124">xs:string</span></span>|<span data-ttu-id="1db2d-125">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1db2d-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1db2d-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1db2d-126">ParentInstanceId</span></span>|<span data-ttu-id="1db2d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-127">xs:string</span></span>|<span data-ttu-id="1db2d-128">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1db2d-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1db2d-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="1db2d-129">ChildActivity</span></span>|<span data-ttu-id="1db2d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-130">xs:string</span></span>|<span data-ttu-id="1db2d-131">已排程之子活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1db2d-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="1db2d-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="1db2d-132">ChildDisplayName</span></span>|<span data-ttu-id="1db2d-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-133">xs:string</span></span>|<span data-ttu-id="1db2d-134">已排程之子活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1db2d-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="1db2d-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="1db2d-135">ChildInstanceId</span></span>|<span data-ttu-id="1db2d-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-136">xs:string</span></span>|<span data-ttu-id="1db2d-137">已排程之子活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1db2d-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="1db2d-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1db2d-138">AppDomain</span></span>|<span data-ttu-id="1db2d-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="1db2d-139">xs:string</span></span>|<span data-ttu-id="1db2d-140">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1db2d-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
