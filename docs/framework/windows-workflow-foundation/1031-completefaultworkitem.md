---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="a7bad-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="a7bad-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a7bad-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a7bad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7bad-104">ID</span><span class="sxs-lookup"><span data-stu-id="a7bad-104">ID</span></span>|<span data-ttu-id="a7bad-105">1031</span><span class="sxs-lookup"><span data-stu-id="a7bad-105">1031</span></span>|  
|<span data-ttu-id="a7bad-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a7bad-106">Keywords</span></span>|<span data-ttu-id="a7bad-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a7bad-107">WFRuntime</span></span>|  
|<span data-ttu-id="a7bad-108">層級</span><span class="sxs-lookup"><span data-stu-id="a7bad-108">Level</span></span>|<span data-ttu-id="a7bad-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a7bad-109">Verbose</span></span>|  
|<span data-ttu-id="a7bad-110">通道</span><span class="sxs-lookup"><span data-stu-id="a7bad-110">Channel</span></span>|<span data-ttu-id="a7bad-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a7bad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a7bad-112">描述</span><span class="sxs-lookup"><span data-stu-id="a7bad-112">Description</span></span>  
 <span data-ttu-id="a7bad-113">表示 FaultWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="a7bad-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a7bad-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a7bad-114">Message</span></span>  
 <span data-ttu-id="a7bad-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="a7bad-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="a7bad-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a7bad-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a7bad-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a7bad-117">Details</span></span>  
  
|<span data-ttu-id="a7bad-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a7bad-118">Data Item Name</span></span>|<span data-ttu-id="a7bad-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a7bad-119">Data Item Type</span></span>|<span data-ttu-id="a7bad-120">描述</span><span class="sxs-lookup"><span data-stu-id="a7bad-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a7bad-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="a7bad-121">FaultActivity</span></span>|<span data-ttu-id="a7bad-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-122">xs:string</span></span>|<span data-ttu-id="a7bad-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a7bad-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="a7bad-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="a7bad-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="a7bad-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-125">xs:string</span></span>|<span data-ttu-id="a7bad-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a7bad-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="a7bad-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="a7bad-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="a7bad-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-128">xs:string</span></span>|<span data-ttu-id="a7bad-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="a7bad-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="a7bad-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="a7bad-130">ExceptionActivity</span></span>|<span data-ttu-id="a7bad-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-131">xs:string</span></span>|<span data-ttu-id="a7bad-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a7bad-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="a7bad-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="a7bad-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="a7bad-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-134">xs:string</span></span>|<span data-ttu-id="a7bad-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a7bad-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="a7bad-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="a7bad-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="a7bad-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-137">xs:string</span></span>|<span data-ttu-id="a7bad-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="a7bad-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="a7bad-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="a7bad-139">Exception</span></span>|<span data-ttu-id="a7bad-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-140">xs:string</span></span>|<span data-ttu-id="a7bad-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="a7bad-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="a7bad-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a7bad-142">AppDomain</span></span>|<span data-ttu-id="a7bad-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7bad-143">xs:string</span></span>|<span data-ttu-id="a7bad-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a7bad-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
