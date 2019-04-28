---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924718"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="0e155-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="0e155-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0e155-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0e155-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e155-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="0e155-104">ID</span></span>|<span data-ttu-id="0e155-105">1022</span><span class="sxs-lookup"><span data-stu-id="0e155-105">1022</span></span>|  
|<span data-ttu-id="0e155-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0e155-106">Keywords</span></span>|<span data-ttu-id="0e155-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0e155-107">WFRuntime</span></span>|  
|<span data-ttu-id="0e155-108">層級</span><span class="sxs-lookup"><span data-stu-id="0e155-108">Level</span></span>|<span data-ttu-id="0e155-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0e155-109">Verbose</span></span>|  
|<span data-ttu-id="0e155-110">通道</span><span class="sxs-lookup"><span data-stu-id="0e155-110">Channel</span></span>|<span data-ttu-id="0e155-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0e155-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0e155-112">描述</span><span class="sxs-lookup"><span data-stu-id="0e155-112">Description</span></span>  
 <span data-ttu-id="0e155-113">表示 BookmarkWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="0e155-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0e155-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0e155-114">Message</span></span>  
 <span data-ttu-id="0e155-115">開始執行 Bookmarkworkitem。bookmarkname:%4、bookmarkscope:%5 活動 '%1'，DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="0e155-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0e155-116">BookmarkName：%4、BookmarkScope：%5。</span><span class="sxs-lookup"><span data-stu-id="0e155-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0e155-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0e155-117">Details</span></span>  
  
|<span data-ttu-id="0e155-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0e155-118">Data Item Name</span></span>|<span data-ttu-id="0e155-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0e155-119">Data Item Type</span></span>|<span data-ttu-id="0e155-120">描述</span><span class="sxs-lookup"><span data-stu-id="0e155-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0e155-121">活動</span><span class="sxs-lookup"><span data-stu-id="0e155-121">Activity</span></span>|<span data-ttu-id="0e155-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e155-122">xs:string</span></span>|<span data-ttu-id="0e155-123">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0e155-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="0e155-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0e155-124">DisplayName</span></span>|<span data-ttu-id="0e155-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e155-125">xs:string</span></span>|<span data-ttu-id="0e155-126">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0e155-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="0e155-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0e155-127">InstanceId</span></span>|<span data-ttu-id="0e155-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e155-128">xs:string</span></span>|<span data-ttu-id="0e155-129">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0e155-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0e155-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="0e155-130">BookmarkName</span></span>|<span data-ttu-id="0e155-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e155-131">xs:string</span></span>|<span data-ttu-id="0e155-132">書籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e155-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="0e155-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="0e155-133">BookmarkScope</span></span>|<span data-ttu-id="0e155-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e155-134">xs:string</span></span>|<span data-ttu-id="0e155-135">書籤的範圍。</span><span class="sxs-lookup"><span data-stu-id="0e155-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="0e155-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0e155-136">AppDomain</span></span>|<span data-ttu-id="0e155-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e155-137">xs:string</span></span>|<span data-ttu-id="0e155-138">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0e155-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
