---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 42ed23654622e29df8ffc210c8d5ba572fa69fd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275345"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="5d8d7-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="5d8d7-102">1021 - ScheduleBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="5d8d7-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5d8d7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d8d7-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="5d8d7-104">ID</span></span>|<span data-ttu-id="5d8d7-105">1021</span><span class="sxs-lookup"><span data-stu-id="5d8d7-105">1021</span></span>|  
|<span data-ttu-id="5d8d7-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5d8d7-106">Keywords</span></span>|<span data-ttu-id="5d8d7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5d8d7-107">WFRuntime</span></span>|  
|<span data-ttu-id="5d8d7-108">層級</span><span class="sxs-lookup"><span data-stu-id="5d8d7-108">Level</span></span>|<span data-ttu-id="5d8d7-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="5d8d7-109">Verbose</span></span>|  
|<span data-ttu-id="5d8d7-110">通路</span><span class="sxs-lookup"><span data-stu-id="5d8d7-110">Channel</span></span>|<span data-ttu-id="5d8d7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5d8d7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5d8d7-112">描述</span><span class="sxs-lookup"><span data-stu-id="5d8d7-112">Description</span></span>  

 <span data-ttu-id="5d8d7-113">表示已排定 BookmarkWorkItem。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5d8d7-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5d8d7-114">Message</span></span>  

 <span data-ttu-id="5d8d7-115">已排定活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 的 BookmarkWorkItem。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5d8d7-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5d8d7-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d8d7-117">Details</span></span>  
  
|<span data-ttu-id="5d8d7-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5d8d7-118">Data Item Name</span></span>|<span data-ttu-id="5d8d7-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5d8d7-119">Data Item Type</span></span>|<span data-ttu-id="5d8d7-120">描述</span><span class="sxs-lookup"><span data-stu-id="5d8d7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5d8d7-121">活動</span><span class="sxs-lookup"><span data-stu-id="5d8d7-121">Activity</span></span>|<span data-ttu-id="5d8d7-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d8d7-122">xs:string</span></span>|<span data-ttu-id="5d8d7-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="5d8d7-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5d8d7-124">DisplayName</span></span>|<span data-ttu-id="5d8d7-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d8d7-125">xs:string</span></span>|<span data-ttu-id="5d8d7-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="5d8d7-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5d8d7-127">InstanceId</span></span>|<span data-ttu-id="5d8d7-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d8d7-128">xs:string</span></span>|<span data-ttu-id="5d8d7-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5d8d7-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="5d8d7-130">BookmarkName</span></span>|<span data-ttu-id="5d8d7-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d8d7-131">xs:string</span></span>|<span data-ttu-id="5d8d7-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="5d8d7-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="5d8d7-133">BookmarkScope</span></span>|<span data-ttu-id="5d8d7-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d8d7-134">xs:string</span></span>|<span data-ttu-id="5d8d7-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="5d8d7-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5d8d7-136">AppDomain</span></span>|<span data-ttu-id="5d8d7-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="5d8d7-137">xs:string</span></span>|<span data-ttu-id="5d8d7-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5d8d7-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
