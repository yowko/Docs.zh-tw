---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509752"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="3cef5-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="3cef5-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3cef5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3cef5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cef5-104">ID</span><span class="sxs-lookup"><span data-stu-id="3cef5-104">ID</span></span>|<span data-ttu-id="3cef5-105">1021</span><span class="sxs-lookup"><span data-stu-id="3cef5-105">1021</span></span>|  
|<span data-ttu-id="3cef5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3cef5-106">Keywords</span></span>|<span data-ttu-id="3cef5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3cef5-107">WFRuntime</span></span>|  
|<span data-ttu-id="3cef5-108">層級</span><span class="sxs-lookup"><span data-stu-id="3cef5-108">Level</span></span>|<span data-ttu-id="3cef5-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="3cef5-109">Verbose</span></span>|  
|<span data-ttu-id="3cef5-110">通道</span><span class="sxs-lookup"><span data-stu-id="3cef5-110">Channel</span></span>|<span data-ttu-id="3cef5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3cef5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3cef5-112">描述</span><span class="sxs-lookup"><span data-stu-id="3cef5-112">Description</span></span>  
 <span data-ttu-id="3cef5-113">表示已排定 BookmarkWorkItem。</span><span class="sxs-lookup"><span data-stu-id="3cef5-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3cef5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3cef5-114">Message</span></span>  
 <span data-ttu-id="3cef5-115">BookmarkWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="3cef5-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="3cef5-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="3cef5-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3cef5-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3cef5-117">Details</span></span>  
  
|<span data-ttu-id="3cef5-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3cef5-118">Data Item Name</span></span>|<span data-ttu-id="3cef5-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3cef5-119">Data Item Type</span></span>|<span data-ttu-id="3cef5-120">描述</span><span class="sxs-lookup"><span data-stu-id="3cef5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3cef5-121">活動</span><span class="sxs-lookup"><span data-stu-id="3cef5-121">Activity</span></span>|<span data-ttu-id="3cef5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cef5-122">xs:string</span></span>|<span data-ttu-id="3cef5-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="3cef5-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="3cef5-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3cef5-124">DisplayName</span></span>|<span data-ttu-id="3cef5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cef5-125">xs:string</span></span>|<span data-ttu-id="3cef5-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3cef5-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="3cef5-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3cef5-127">InstanceId</span></span>|<span data-ttu-id="3cef5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cef5-128">xs:string</span></span>|<span data-ttu-id="3cef5-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="3cef5-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3cef5-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="3cef5-130">BookmarkName</span></span>|<span data-ttu-id="3cef5-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cef5-131">xs:string</span></span>|<span data-ttu-id="3cef5-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cef5-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="3cef5-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="3cef5-133">BookmarkScope</span></span>|<span data-ttu-id="3cef5-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cef5-134">xs:string</span></span>|<span data-ttu-id="3cef5-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="3cef5-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="3cef5-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3cef5-136">AppDomain</span></span>|<span data-ttu-id="3cef5-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="3cef5-137">xs:string</span></span>|<span data-ttu-id="3cef5-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3cef5-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
