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
ms.workload: dotnet
ms.openlocfilehash: a87ecb0a50437d83dd3c80d213553c8ac2143968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="56491-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="56491-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="56491-103">屬性</span><span class="sxs-lookup"><span data-stu-id="56491-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56491-104">ID</span><span class="sxs-lookup"><span data-stu-id="56491-104">ID</span></span>|<span data-ttu-id="56491-105">1031</span><span class="sxs-lookup"><span data-stu-id="56491-105">1031</span></span>|  
|<span data-ttu-id="56491-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="56491-106">Keywords</span></span>|<span data-ttu-id="56491-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="56491-107">WFRuntime</span></span>|  
|<span data-ttu-id="56491-108">層級</span><span class="sxs-lookup"><span data-stu-id="56491-108">Level</span></span>|<span data-ttu-id="56491-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="56491-109">Verbose</span></span>|  
|<span data-ttu-id="56491-110">通道</span><span class="sxs-lookup"><span data-stu-id="56491-110">Channel</span></span>|<span data-ttu-id="56491-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="56491-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="56491-112">描述</span><span class="sxs-lookup"><span data-stu-id="56491-112">Description</span></span>  
 <span data-ttu-id="56491-113">表示 FaultWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="56491-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="56491-114">訊息</span><span class="sxs-lookup"><span data-stu-id="56491-114">Message</span></span>  
 <span data-ttu-id="56491-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="56491-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="56491-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56491-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="56491-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="56491-117">Details</span></span>  
  
|<span data-ttu-id="56491-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="56491-118">Data Item Name</span></span>|<span data-ttu-id="56491-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="56491-119">Data Item Type</span></span>|<span data-ttu-id="56491-120">描述</span><span class="sxs-lookup"><span data-stu-id="56491-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="56491-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="56491-121">FaultActivity</span></span>|<span data-ttu-id="56491-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-122">xs:string</span></span>|<span data-ttu-id="56491-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="56491-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="56491-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="56491-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="56491-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-125">xs:string</span></span>|<span data-ttu-id="56491-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="56491-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="56491-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="56491-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="56491-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-128">xs:string</span></span>|<span data-ttu-id="56491-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="56491-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="56491-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="56491-130">ExceptionActivity</span></span>|<span data-ttu-id="56491-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-131">xs:string</span></span>|<span data-ttu-id="56491-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="56491-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="56491-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="56491-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="56491-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-134">xs:string</span></span>|<span data-ttu-id="56491-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="56491-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="56491-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="56491-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="56491-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-137">xs:string</span></span>|<span data-ttu-id="56491-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="56491-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="56491-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="56491-139">Exception</span></span>|<span data-ttu-id="56491-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-140">xs:string</span></span>|<span data-ttu-id="56491-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="56491-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="56491-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="56491-142">AppDomain</span></span>|<span data-ttu-id="56491-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="56491-143">xs:string</span></span>|<span data-ttu-id="56491-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="56491-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
