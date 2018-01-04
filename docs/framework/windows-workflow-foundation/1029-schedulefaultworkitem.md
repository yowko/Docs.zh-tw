---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfa9553c25f607ec25fd968c2e8c6db061fb49dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="fadea-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="fadea-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fadea-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fadea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fadea-104">ID</span><span class="sxs-lookup"><span data-stu-id="fadea-104">ID</span></span>|<span data-ttu-id="fadea-105">1029</span><span class="sxs-lookup"><span data-stu-id="fadea-105">1029</span></span>|  
|<span data-ttu-id="fadea-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fadea-106">Keywords</span></span>|<span data-ttu-id="fadea-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fadea-107">WFRuntime</span></span>|  
|<span data-ttu-id="fadea-108">層級</span><span class="sxs-lookup"><span data-stu-id="fadea-108">Level</span></span>|<span data-ttu-id="fadea-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fadea-109">Verbose</span></span>|  
|<span data-ttu-id="fadea-110">通道</span><span class="sxs-lookup"><span data-stu-id="fadea-110">Channel</span></span>|<span data-ttu-id="fadea-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fadea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fadea-112">描述</span><span class="sxs-lookup"><span data-stu-id="fadea-112">Description</span></span>  
 <span data-ttu-id="fadea-113">表示已排定 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="fadea-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fadea-114">訊息</span><span class="sxs-lookup"><span data-stu-id="fadea-114">Message</span></span>  
 <span data-ttu-id="fadea-115">FaultWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="fadea-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="fadea-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fadea-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fadea-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fadea-117">Details</span></span>  
  
|<span data-ttu-id="fadea-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fadea-118">Data Item Name</span></span>|<span data-ttu-id="fadea-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fadea-119">Data Item Type</span></span>|<span data-ttu-id="fadea-120">描述</span><span class="sxs-lookup"><span data-stu-id="fadea-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fadea-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="fadea-121">FaultActivity</span></span>|<span data-ttu-id="fadea-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-122">xs:string</span></span>|<span data-ttu-id="fadea-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fadea-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="fadea-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fadea-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="fadea-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-125">xs:string</span></span>|<span data-ttu-id="fadea-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="fadea-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="fadea-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fadea-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="fadea-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-128">xs:string</span></span>|<span data-ttu-id="fadea-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="fadea-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="fadea-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="fadea-130">ExceptionActivity</span></span>|<span data-ttu-id="fadea-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-131">xs:string</span></span>|<span data-ttu-id="fadea-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fadea-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fadea-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fadea-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="fadea-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-134">xs:string</span></span>|<span data-ttu-id="fadea-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="fadea-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fadea-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fadea-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="fadea-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-137">xs:string</span></span>|<span data-ttu-id="fadea-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="fadea-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fadea-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="fadea-139">Exception</span></span>|<span data-ttu-id="fadea-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-140">xs:string</span></span>|<span data-ttu-id="fadea-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="fadea-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="fadea-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fadea-142">AppDomain</span></span>|<span data-ttu-id="fadea-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="fadea-143">xs:string</span></span>|<span data-ttu-id="fadea-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fadea-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
