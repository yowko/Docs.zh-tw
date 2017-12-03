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
ms.openlocfilehash: 781f4b6d064ac90f762e10e03783422c64a1bf05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="37bb6-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="37bb6-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="37bb6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="37bb6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="37bb6-104">ID</span><span class="sxs-lookup"><span data-stu-id="37bb6-104">ID</span></span>|<span data-ttu-id="37bb6-105">1021</span><span class="sxs-lookup"><span data-stu-id="37bb6-105">1021</span></span>|  
|<span data-ttu-id="37bb6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="37bb6-106">Keywords</span></span>|<span data-ttu-id="37bb6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="37bb6-107">WFRuntime</span></span>|  
|<span data-ttu-id="37bb6-108">層級</span><span class="sxs-lookup"><span data-stu-id="37bb6-108">Level</span></span>|<span data-ttu-id="37bb6-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="37bb6-109">Verbose</span></span>|  
|<span data-ttu-id="37bb6-110">通道</span><span class="sxs-lookup"><span data-stu-id="37bb6-110">Channel</span></span>|<span data-ttu-id="37bb6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="37bb6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="37bb6-112">描述</span><span class="sxs-lookup"><span data-stu-id="37bb6-112">Description</span></span>  
 <span data-ttu-id="37bb6-113">表示已排定 BookmarkWorkItem。</span><span class="sxs-lookup"><span data-stu-id="37bb6-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="37bb6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="37bb6-114">Message</span></span>  
 <span data-ttu-id="37bb6-115">BookmarkWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="37bb6-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="37bb6-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="37bb6-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="37bb6-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="37bb6-117">Details</span></span>  
  
|<span data-ttu-id="37bb6-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="37bb6-118">Data Item Name</span></span>|<span data-ttu-id="37bb6-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="37bb6-119">Data Item Type</span></span>|<span data-ttu-id="37bb6-120">描述</span><span class="sxs-lookup"><span data-stu-id="37bb6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="37bb6-121">活動</span><span class="sxs-lookup"><span data-stu-id="37bb6-121">Activity</span></span>|<span data-ttu-id="37bb6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="37bb6-122">xs:string</span></span>|<span data-ttu-id="37bb6-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="37bb6-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="37bb6-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="37bb6-124">DisplayName</span></span>|<span data-ttu-id="37bb6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="37bb6-125">xs:string</span></span>|<span data-ttu-id="37bb6-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="37bb6-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="37bb6-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="37bb6-127">InstanceId</span></span>|<span data-ttu-id="37bb6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="37bb6-128">xs:string</span></span>|<span data-ttu-id="37bb6-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="37bb6-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="37bb6-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="37bb6-130">BookmarkName</span></span>|<span data-ttu-id="37bb6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="37bb6-131">xs:string</span></span>|<span data-ttu-id="37bb6-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="37bb6-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="37bb6-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="37bb6-133">BookmarkScope</span></span>|<span data-ttu-id="37bb6-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="37bb6-134">xs:string</span></span>|<span data-ttu-id="37bb6-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="37bb6-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="37bb6-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="37bb6-136">AppDomain</span></span>|<span data-ttu-id="37bb6-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="37bb6-137">xs:string</span></span>|<span data-ttu-id="37bb6-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="37bb6-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
