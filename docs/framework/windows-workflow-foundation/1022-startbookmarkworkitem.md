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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aaabbdca455d31d22b232ae2b08edef0687ac30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="38f4d-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="38f4d-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="38f4d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="38f4d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38f4d-104">ID</span><span class="sxs-lookup"><span data-stu-id="38f4d-104">ID</span></span>|<span data-ttu-id="38f4d-105">1022</span><span class="sxs-lookup"><span data-stu-id="38f4d-105">1022</span></span>|  
|<span data-ttu-id="38f4d-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="38f4d-106">Keywords</span></span>|<span data-ttu-id="38f4d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="38f4d-107">WFRuntime</span></span>|  
|<span data-ttu-id="38f4d-108">層級</span><span class="sxs-lookup"><span data-stu-id="38f4d-108">Level</span></span>|<span data-ttu-id="38f4d-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="38f4d-109">Verbose</span></span>|  
|<span data-ttu-id="38f4d-110">通道</span><span class="sxs-lookup"><span data-stu-id="38f4d-110">Channel</span></span>|<span data-ttu-id="38f4d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="38f4d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="38f4d-112">描述</span><span class="sxs-lookup"><span data-stu-id="38f4d-112">Description</span></span>  
 <span data-ttu-id="38f4d-113">表示 BookmarkWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="38f4d-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="38f4d-114">訊息</span><span class="sxs-lookup"><span data-stu-id="38f4d-114">Message</span></span>  
 <span data-ttu-id="38f4d-115">開始執行的 bookmarkworkitem 活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="38f4d-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="38f4d-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="38f4d-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="38f4d-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="38f4d-117">Details</span></span>  
  
|<span data-ttu-id="38f4d-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="38f4d-118">Data Item Name</span></span>|<span data-ttu-id="38f4d-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="38f4d-119">Data Item Type</span></span>|<span data-ttu-id="38f4d-120">描述</span><span class="sxs-lookup"><span data-stu-id="38f4d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="38f4d-121">活動</span><span class="sxs-lookup"><span data-stu-id="38f4d-121">Activity</span></span>|<span data-ttu-id="38f4d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="38f4d-122">xs:string</span></span>|<span data-ttu-id="38f4d-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="38f4d-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="38f4d-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="38f4d-124">DisplayName</span></span>|<span data-ttu-id="38f4d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="38f4d-125">xs:string</span></span>|<span data-ttu-id="38f4d-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="38f4d-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="38f4d-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="38f4d-127">InstanceId</span></span>|<span data-ttu-id="38f4d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="38f4d-128">xs:string</span></span>|<span data-ttu-id="38f4d-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="38f4d-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="38f4d-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="38f4d-130">BookmarkName</span></span>|<span data-ttu-id="38f4d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="38f4d-131">xs:string</span></span>|<span data-ttu-id="38f4d-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="38f4d-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="38f4d-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="38f4d-133">BookmarkScope</span></span>|<span data-ttu-id="38f4d-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="38f4d-134">xs:string</span></span>|<span data-ttu-id="38f4d-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="38f4d-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="38f4d-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="38f4d-136">AppDomain</span></span>|<span data-ttu-id="38f4d-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="38f4d-137">xs:string</span></span>|<span data-ttu-id="38f4d-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="38f4d-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
