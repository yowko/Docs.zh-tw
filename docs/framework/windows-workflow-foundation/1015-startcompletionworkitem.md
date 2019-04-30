---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032262"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="07002-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="07002-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="07002-103">屬性</span><span class="sxs-lookup"><span data-stu-id="07002-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07002-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="07002-104">ID</span></span>|<span data-ttu-id="07002-105">1015</span><span class="sxs-lookup"><span data-stu-id="07002-105">1015</span></span>|  
|<span data-ttu-id="07002-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="07002-106">Keywords</span></span>|<span data-ttu-id="07002-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="07002-107">WFRuntime</span></span>|  
|<span data-ttu-id="07002-108">層級</span><span class="sxs-lookup"><span data-stu-id="07002-108">Level</span></span>|<span data-ttu-id="07002-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="07002-109">Verbose</span></span>|  
|<span data-ttu-id="07002-110">通道</span><span class="sxs-lookup"><span data-stu-id="07002-110">Channel</span></span>|<span data-ttu-id="07002-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="07002-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="07002-112">描述</span><span class="sxs-lookup"><span data-stu-id="07002-112">Description</span></span>  
 <span data-ttu-id="07002-113">表示 CompletionWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="07002-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="07002-114">訊息</span><span class="sxs-lookup"><span data-stu-id="07002-114">Message</span></span>  
 <span data-ttu-id="07002-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="07002-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="07002-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="07002-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="07002-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="07002-117">Details</span></span>  
  
|<span data-ttu-id="07002-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="07002-118">Data Item Name</span></span>|<span data-ttu-id="07002-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="07002-119">Data Item Type</span></span>|<span data-ttu-id="07002-120">描述</span><span class="sxs-lookup"><span data-stu-id="07002-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="07002-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="07002-121">ParentActivity</span></span>|<span data-ttu-id="07002-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-122">xs:string</span></span>|<span data-ttu-id="07002-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="07002-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="07002-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="07002-124">ParentDisplayName</span></span>|<span data-ttu-id="07002-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-125">xs:string</span></span>|<span data-ttu-id="07002-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="07002-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="07002-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="07002-127">ParentInstanceId</span></span>|<span data-ttu-id="07002-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-128">xs:string</span></span>|<span data-ttu-id="07002-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="07002-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="07002-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="07002-130">CompletedActivity</span></span>|<span data-ttu-id="07002-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-131">xs:string</span></span>|<span data-ttu-id="07002-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="07002-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="07002-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="07002-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="07002-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-134">xs:string</span></span>|<span data-ttu-id="07002-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="07002-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="07002-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="07002-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="07002-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-137">xs:string</span></span>|<span data-ttu-id="07002-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="07002-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="07002-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="07002-139">AppDomain</span></span>|<span data-ttu-id="07002-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="07002-140">xs:string</span></span>|<span data-ttu-id="07002-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="07002-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
