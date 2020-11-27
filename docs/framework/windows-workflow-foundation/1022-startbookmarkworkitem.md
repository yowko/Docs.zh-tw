---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: ca1f4244fb1a5144cb2d86eaacb9b31137d317c2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275332"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="08ffb-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="08ffb-102">1022 - StartBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="08ffb-103">屬性</span><span class="sxs-lookup"><span data-stu-id="08ffb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08ffb-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="08ffb-104">ID</span></span>|<span data-ttu-id="08ffb-105">1022</span><span class="sxs-lookup"><span data-stu-id="08ffb-105">1022</span></span>|  
|<span data-ttu-id="08ffb-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="08ffb-106">Keywords</span></span>|<span data-ttu-id="08ffb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="08ffb-107">WFRuntime</span></span>|  
|<span data-ttu-id="08ffb-108">層級</span><span class="sxs-lookup"><span data-stu-id="08ffb-108">Level</span></span>|<span data-ttu-id="08ffb-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="08ffb-109">Verbose</span></span>|  
|<span data-ttu-id="08ffb-110">通路</span><span class="sxs-lookup"><span data-stu-id="08ffb-110">Channel</span></span>|<span data-ttu-id="08ffb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="08ffb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08ffb-112">描述</span><span class="sxs-lookup"><span data-stu-id="08ffb-112">Description</span></span>  

 <span data-ttu-id="08ffb-113">表示 BookmarkWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="08ffb-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08ffb-114">訊息</span><span class="sxs-lookup"><span data-stu-id="08ffb-114">Message</span></span>  

 <span data-ttu-id="08ffb-115">開始執行活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 的 BookmarkWorkItem。</span><span class="sxs-lookup"><span data-stu-id="08ffb-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="08ffb-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="08ffb-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08ffb-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="08ffb-117">Details</span></span>  
  
|<span data-ttu-id="08ffb-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="08ffb-118">Data Item Name</span></span>|<span data-ttu-id="08ffb-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="08ffb-119">Data Item Type</span></span>|<span data-ttu-id="08ffb-120">描述</span><span class="sxs-lookup"><span data-stu-id="08ffb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08ffb-121">活動</span><span class="sxs-lookup"><span data-stu-id="08ffb-121">Activity</span></span>|<span data-ttu-id="08ffb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="08ffb-122">xs:string</span></span>|<span data-ttu-id="08ffb-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="08ffb-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="08ffb-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="08ffb-124">DisplayName</span></span>|<span data-ttu-id="08ffb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="08ffb-125">xs:string</span></span>|<span data-ttu-id="08ffb-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="08ffb-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="08ffb-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="08ffb-127">InstanceId</span></span>|<span data-ttu-id="08ffb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="08ffb-128">xs:string</span></span>|<span data-ttu-id="08ffb-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="08ffb-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="08ffb-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="08ffb-130">BookmarkName</span></span>|<span data-ttu-id="08ffb-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="08ffb-131">xs:string</span></span>|<span data-ttu-id="08ffb-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="08ffb-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="08ffb-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="08ffb-133">BookmarkScope</span></span>|<span data-ttu-id="08ffb-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="08ffb-134">xs:string</span></span>|<span data-ttu-id="08ffb-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="08ffb-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="08ffb-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="08ffb-136">AppDomain</span></span>|<span data-ttu-id="08ffb-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="08ffb-137">xs:string</span></span>|<span data-ttu-id="08ffb-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="08ffb-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
