---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61c67792f807907f58480f3bfa3d192b811766b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="00d69-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="00d69-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="00d69-103">屬性</span><span class="sxs-lookup"><span data-stu-id="00d69-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00d69-104">ID</span><span class="sxs-lookup"><span data-stu-id="00d69-104">ID</span></span>|<span data-ttu-id="00d69-105">1021</span><span class="sxs-lookup"><span data-stu-id="00d69-105">1021</span></span>|  
|<span data-ttu-id="00d69-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="00d69-106">Keywords</span></span>|<span data-ttu-id="00d69-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="00d69-107">WFRuntime</span></span>|  
|<span data-ttu-id="00d69-108">層級</span><span class="sxs-lookup"><span data-stu-id="00d69-108">Level</span></span>|<span data-ttu-id="00d69-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="00d69-109">Verbose</span></span>|  
|<span data-ttu-id="00d69-110">通道</span><span class="sxs-lookup"><span data-stu-id="00d69-110">Channel</span></span>|<span data-ttu-id="00d69-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="00d69-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="00d69-112">描述</span><span class="sxs-lookup"><span data-stu-id="00d69-112">Description</span></span>  
 <span data-ttu-id="00d69-113">表示已排定 BookmarkWorkItem。</span><span class="sxs-lookup"><span data-stu-id="00d69-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="00d69-114">訊息</span><span class="sxs-lookup"><span data-stu-id="00d69-114">Message</span></span>  
 <span data-ttu-id="00d69-115">BookmarkWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="00d69-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="00d69-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="00d69-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="00d69-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00d69-117">Details</span></span>  
  
|<span data-ttu-id="00d69-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="00d69-118">Data Item Name</span></span>|<span data-ttu-id="00d69-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="00d69-119">Data Item Type</span></span>|<span data-ttu-id="00d69-120">描述</span><span class="sxs-lookup"><span data-stu-id="00d69-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="00d69-121">活動</span><span class="sxs-lookup"><span data-stu-id="00d69-121">Activity</span></span>|<span data-ttu-id="00d69-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="00d69-122">xs:string</span></span>|<span data-ttu-id="00d69-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="00d69-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="00d69-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="00d69-124">DisplayName</span></span>|<span data-ttu-id="00d69-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="00d69-125">xs:string</span></span>|<span data-ttu-id="00d69-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="00d69-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="00d69-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="00d69-127">InstanceId</span></span>|<span data-ttu-id="00d69-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="00d69-128">xs:string</span></span>|<span data-ttu-id="00d69-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="00d69-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="00d69-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="00d69-130">BookmarkName</span></span>|<span data-ttu-id="00d69-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="00d69-131">xs:string</span></span>|<span data-ttu-id="00d69-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="00d69-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="00d69-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="00d69-133">BookmarkScope</span></span>|<span data-ttu-id="00d69-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="00d69-134">xs:string</span></span>|<span data-ttu-id="00d69-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="00d69-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="00d69-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="00d69-136">AppDomain</span></span>|<span data-ttu-id="00d69-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="00d69-137">xs:string</span></span>|<span data-ttu-id="00d69-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="00d69-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
