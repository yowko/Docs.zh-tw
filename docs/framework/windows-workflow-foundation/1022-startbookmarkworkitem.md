---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdb6af10c45e7a93e9a68e6150e5d239002cce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="c82e6-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="c82e6-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c82e6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c82e6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c82e6-104">ID</span><span class="sxs-lookup"><span data-stu-id="c82e6-104">ID</span></span>|<span data-ttu-id="c82e6-105">1022</span><span class="sxs-lookup"><span data-stu-id="c82e6-105">1022</span></span>|  
|<span data-ttu-id="c82e6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c82e6-106">Keywords</span></span>|<span data-ttu-id="c82e6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c82e6-107">WFRuntime</span></span>|  
|<span data-ttu-id="c82e6-108">層級</span><span class="sxs-lookup"><span data-stu-id="c82e6-108">Level</span></span>|<span data-ttu-id="c82e6-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c82e6-109">Verbose</span></span>|  
|<span data-ttu-id="c82e6-110">通道</span><span class="sxs-lookup"><span data-stu-id="c82e6-110">Channel</span></span>|<span data-ttu-id="c82e6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c82e6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c82e6-112">描述</span><span class="sxs-lookup"><span data-stu-id="c82e6-112">Description</span></span>  
 <span data-ttu-id="c82e6-113">表示 BookmarkWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="c82e6-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c82e6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c82e6-114">Message</span></span>  
 <span data-ttu-id="c82e6-115">開始執行的 bookmarkworkitem 活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="c82e6-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c82e6-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="c82e6-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c82e6-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c82e6-117">Details</span></span>  
  
|<span data-ttu-id="c82e6-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c82e6-118">Data Item Name</span></span>|<span data-ttu-id="c82e6-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c82e6-119">Data Item Type</span></span>|<span data-ttu-id="c82e6-120">描述</span><span class="sxs-lookup"><span data-stu-id="c82e6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c82e6-121">活動</span><span class="sxs-lookup"><span data-stu-id="c82e6-121">Activity</span></span>|<span data-ttu-id="c82e6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c82e6-122">xs:string</span></span>|<span data-ttu-id="c82e6-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c82e6-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="c82e6-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c82e6-124">DisplayName</span></span>|<span data-ttu-id="c82e6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c82e6-125">xs:string</span></span>|<span data-ttu-id="c82e6-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c82e6-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="c82e6-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c82e6-127">InstanceId</span></span>|<span data-ttu-id="c82e6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c82e6-128">xs:string</span></span>|<span data-ttu-id="c82e6-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c82e6-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c82e6-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="c82e6-130">BookmarkName</span></span>|<span data-ttu-id="c82e6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c82e6-131">xs:string</span></span>|<span data-ttu-id="c82e6-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="c82e6-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="c82e6-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="c82e6-133">BookmarkScope</span></span>|<span data-ttu-id="c82e6-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c82e6-134">xs:string</span></span>|<span data-ttu-id="c82e6-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="c82e6-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="c82e6-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c82e6-136">AppDomain</span></span>|<span data-ttu-id="c82e6-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c82e6-137">xs:string</span></span>|<span data-ttu-id="c82e6-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c82e6-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
