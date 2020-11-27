---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 8c9c20fd4fb74f80779c1d2ef8f29ac3d44050d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275371"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="264f5-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="264f5-102">1020 - CreateBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="264f5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="264f5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="264f5-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="264f5-104">ID</span></span>|<span data-ttu-id="264f5-105">1020</span><span class="sxs-lookup"><span data-stu-id="264f5-105">1020</span></span>|  
|<span data-ttu-id="264f5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="264f5-106">Keywords</span></span>|<span data-ttu-id="264f5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="264f5-107">WFRuntime</span></span>|  
|<span data-ttu-id="264f5-108">層級</span><span class="sxs-lookup"><span data-stu-id="264f5-108">Level</span></span>|<span data-ttu-id="264f5-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="264f5-109">Verbose</span></span>|  
|<span data-ttu-id="264f5-110">通路</span><span class="sxs-lookup"><span data-stu-id="264f5-110">Channel</span></span>|<span data-ttu-id="264f5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="264f5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="264f5-112">描述</span><span class="sxs-lookup"><span data-stu-id="264f5-112">Description</span></span>  

 <span data-ttu-id="264f5-113">表示已經為活動建立書籤。</span><span class="sxs-lookup"><span data-stu-id="264f5-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="264f5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="264f5-114">Message</span></span>  

 <span data-ttu-id="264f5-115">已為活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 建立書簽。</span><span class="sxs-lookup"><span data-stu-id="264f5-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="264f5-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="264f5-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="264f5-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="264f5-117">Details</span></span>  
  
|<span data-ttu-id="264f5-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="264f5-118">Data Item Name</span></span>|<span data-ttu-id="264f5-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="264f5-119">Data Item Type</span></span>|<span data-ttu-id="264f5-120">描述</span><span class="sxs-lookup"><span data-stu-id="264f5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="264f5-121">活動</span><span class="sxs-lookup"><span data-stu-id="264f5-121">Activity</span></span>|<span data-ttu-id="264f5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="264f5-122">xs:string</span></span>|<span data-ttu-id="264f5-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="264f5-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="264f5-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="264f5-124">DisplayName</span></span>|<span data-ttu-id="264f5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="264f5-125">xs:string</span></span>|<span data-ttu-id="264f5-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="264f5-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="264f5-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="264f5-127">InstanceId</span></span>|<span data-ttu-id="264f5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="264f5-128">xs:string</span></span>|<span data-ttu-id="264f5-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="264f5-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="264f5-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="264f5-130">BookmarkName</span></span>|<span data-ttu-id="264f5-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="264f5-131">xs:string</span></span>|<span data-ttu-id="264f5-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="264f5-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="264f5-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="264f5-133">BookmarkScope</span></span>|<span data-ttu-id="264f5-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="264f5-134">xs:string</span></span>|<span data-ttu-id="264f5-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="264f5-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="264f5-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="264f5-136">AppDomain</span></span>|<span data-ttu-id="264f5-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="264f5-137">xs:string</span></span>|<span data-ttu-id="264f5-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="264f5-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
