---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 436a0323fcf4498a1d707f7af9bd8204885fd645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="9e8d2-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="9e8d2-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9e8d2-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9e8d2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e8d2-104">ID</span><span class="sxs-lookup"><span data-stu-id="9e8d2-104">ID</span></span>|<span data-ttu-id="9e8d2-105">1030</span><span class="sxs-lookup"><span data-stu-id="9e8d2-105">1030</span></span>|  
|<span data-ttu-id="9e8d2-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9e8d2-106">Keywords</span></span>|<span data-ttu-id="9e8d2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9e8d2-107">WFRuntime</span></span>|  
|<span data-ttu-id="9e8d2-108">層級</span><span class="sxs-lookup"><span data-stu-id="9e8d2-108">Level</span></span>|<span data-ttu-id="9e8d2-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9e8d2-109">Verbose</span></span>|  
|<span data-ttu-id="9e8d2-110">通道</span><span class="sxs-lookup"><span data-stu-id="9e8d2-110">Channel</span></span>|<span data-ttu-id="9e8d2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9e8d2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9e8d2-112">描述</span><span class="sxs-lookup"><span data-stu-id="9e8d2-112">Description</span></span>  
 <span data-ttu-id="9e8d2-113">表示 FaultWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9e8d2-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9e8d2-114">Message</span></span>  
 <span data-ttu-id="9e8d2-115">開始執行的 faultworkitem 活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="9e8d2-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9e8d2-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e8d2-117">Details</span></span>  
  
|<span data-ttu-id="9e8d2-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9e8d2-118">Data Item Name</span></span>|<span data-ttu-id="9e8d2-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9e8d2-119">Data Item Type</span></span>|<span data-ttu-id="9e8d2-120">描述</span><span class="sxs-lookup"><span data-stu-id="9e8d2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9e8d2-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="9e8d2-121">FaultActivity</span></span>|<span data-ttu-id="9e8d2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-122">xs:string</span></span>|<span data-ttu-id="9e8d2-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="9e8d2-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9e8d2-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="9e8d2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-125">xs:string</span></span>|<span data-ttu-id="9e8d2-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="9e8d2-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9e8d2-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="9e8d2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-128">xs:string</span></span>|<span data-ttu-id="9e8d2-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="9e8d2-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="9e8d2-130">ExceptionActivity</span></span>|<span data-ttu-id="9e8d2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-131">xs:string</span></span>|<span data-ttu-id="9e8d2-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9e8d2-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9e8d2-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="9e8d2-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-134">xs:string</span></span>|<span data-ttu-id="9e8d2-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9e8d2-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9e8d2-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="9e8d2-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-137">xs:string</span></span>|<span data-ttu-id="9e8d2-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9e8d2-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="9e8d2-139">Exception</span></span>|<span data-ttu-id="9e8d2-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-140">xs:string</span></span>|<span data-ttu-id="9e8d2-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e8d2-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="9e8d2-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9e8d2-142">AppDomain</span></span>|<span data-ttu-id="9e8d2-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e8d2-143">xs:string</span></span>|<span data-ttu-id="9e8d2-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9e8d2-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
