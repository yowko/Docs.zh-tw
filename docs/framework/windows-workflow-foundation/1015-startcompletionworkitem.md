---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="c6bd5-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="c6bd5-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c6bd5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c6bd5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6bd5-104">ID</span><span class="sxs-lookup"><span data-stu-id="c6bd5-104">ID</span></span>|<span data-ttu-id="c6bd5-105">1015</span><span class="sxs-lookup"><span data-stu-id="c6bd5-105">1015</span></span>|  
|<span data-ttu-id="c6bd5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c6bd5-106">Keywords</span></span>|<span data-ttu-id="c6bd5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c6bd5-107">WFRuntime</span></span>|  
|<span data-ttu-id="c6bd5-108">層級</span><span class="sxs-lookup"><span data-stu-id="c6bd5-108">Level</span></span>|<span data-ttu-id="c6bd5-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c6bd5-109">Verbose</span></span>|  
|<span data-ttu-id="c6bd5-110">通道</span><span class="sxs-lookup"><span data-stu-id="c6bd5-110">Channel</span></span>|<span data-ttu-id="c6bd5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c6bd5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6bd5-112">描述</span><span class="sxs-lookup"><span data-stu-id="c6bd5-112">Description</span></span>  
 <span data-ttu-id="c6bd5-113">表示 CompletionWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6bd5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c6bd5-114">Message</span></span>  
 <span data-ttu-id="c6bd5-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="c6bd5-116">已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6bd5-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6bd5-117">Details</span></span>  
  
|<span data-ttu-id="c6bd5-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c6bd5-118">Data Item Name</span></span>|<span data-ttu-id="c6bd5-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c6bd5-119">Data Item Type</span></span>|<span data-ttu-id="c6bd5-120">描述</span><span class="sxs-lookup"><span data-stu-id="c6bd5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6bd5-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="c6bd5-121">ParentActivity</span></span>|<span data-ttu-id="c6bd5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-122">xs:string</span></span>|<span data-ttu-id="c6bd5-123">父活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c6bd5-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c6bd5-124">ParentDisplayName</span></span>|<span data-ttu-id="c6bd5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-125">xs:string</span></span>|<span data-ttu-id="c6bd5-126">父活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c6bd5-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c6bd5-127">ParentInstanceId</span></span>|<span data-ttu-id="c6bd5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-128">xs:string</span></span>|<span data-ttu-id="c6bd5-129">父活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c6bd5-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="c6bd5-130">CompletedActivity</span></span>|<span data-ttu-id="c6bd5-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-131">xs:string</span></span>|<span data-ttu-id="c6bd5-132">已完成之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="c6bd5-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c6bd5-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="c6bd5-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-134">xs:string</span></span>|<span data-ttu-id="c6bd5-135">已完成之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="c6bd5-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c6bd5-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="c6bd5-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-137">xs:string</span></span>|<span data-ttu-id="c6bd5-138">已完成之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="c6bd5-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6bd5-139">AppDomain</span></span>|<span data-ttu-id="c6bd5-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6bd5-140">xs:string</span></span>|<span data-ttu-id="c6bd5-141">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c6bd5-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
