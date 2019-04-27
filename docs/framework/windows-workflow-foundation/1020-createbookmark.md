---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924744"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="831bb-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="831bb-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="831bb-103">屬性</span><span class="sxs-lookup"><span data-stu-id="831bb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="831bb-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="831bb-104">ID</span></span>|<span data-ttu-id="831bb-105">1020</span><span class="sxs-lookup"><span data-stu-id="831bb-105">1020</span></span>|  
|<span data-ttu-id="831bb-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="831bb-106">Keywords</span></span>|<span data-ttu-id="831bb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="831bb-107">WFRuntime</span></span>|  
|<span data-ttu-id="831bb-108">層級</span><span class="sxs-lookup"><span data-stu-id="831bb-108">Level</span></span>|<span data-ttu-id="831bb-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="831bb-109">Verbose</span></span>|  
|<span data-ttu-id="831bb-110">通道</span><span class="sxs-lookup"><span data-stu-id="831bb-110">Channel</span></span>|<span data-ttu-id="831bb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="831bb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="831bb-112">描述</span><span class="sxs-lookup"><span data-stu-id="831bb-112">Description</span></span>  
 <span data-ttu-id="831bb-113">表示已經為活動建立書籤。</span><span class="sxs-lookup"><span data-stu-id="831bb-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="831bb-114">訊息</span><span class="sxs-lookup"><span data-stu-id="831bb-114">Message</span></span>  
 <span data-ttu-id="831bb-115">已建立書籤的活動 '%1'，DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="831bb-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="831bb-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="831bb-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="831bb-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="831bb-117">Details</span></span>  
  
|<span data-ttu-id="831bb-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="831bb-118">Data Item Name</span></span>|<span data-ttu-id="831bb-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="831bb-119">Data Item Type</span></span>|<span data-ttu-id="831bb-120">描述</span><span class="sxs-lookup"><span data-stu-id="831bb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="831bb-121">活動</span><span class="sxs-lookup"><span data-stu-id="831bb-121">Activity</span></span>|<span data-ttu-id="831bb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="831bb-122">xs:string</span></span>|<span data-ttu-id="831bb-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="831bb-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="831bb-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="831bb-124">DisplayName</span></span>|<span data-ttu-id="831bb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="831bb-125">xs:string</span></span>|<span data-ttu-id="831bb-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="831bb-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="831bb-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="831bb-127">InstanceId</span></span>|<span data-ttu-id="831bb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="831bb-128">xs:string</span></span>|<span data-ttu-id="831bb-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="831bb-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="831bb-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="831bb-130">BookmarkName</span></span>|<span data-ttu-id="831bb-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="831bb-131">xs:string</span></span>|<span data-ttu-id="831bb-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="831bb-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="831bb-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="831bb-133">BookmarkScope</span></span>|<span data-ttu-id="831bb-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="831bb-134">xs:string</span></span>|<span data-ttu-id="831bb-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="831bb-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="831bb-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="831bb-136">AppDomain</span></span>|<span data-ttu-id="831bb-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="831bb-137">xs:string</span></span>|<span data-ttu-id="831bb-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="831bb-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
