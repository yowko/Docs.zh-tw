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
ms.openlocfilehash: c639de96bd72670b2641707e7283be2642801dbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="42cac-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="42cac-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="42cac-103">屬性</span><span class="sxs-lookup"><span data-stu-id="42cac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42cac-104">ID</span><span class="sxs-lookup"><span data-stu-id="42cac-104">ID</span></span>|<span data-ttu-id="42cac-105">1030</span><span class="sxs-lookup"><span data-stu-id="42cac-105">1030</span></span>|  
|<span data-ttu-id="42cac-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="42cac-106">Keywords</span></span>|<span data-ttu-id="42cac-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="42cac-107">WFRuntime</span></span>|  
|<span data-ttu-id="42cac-108">層級</span><span class="sxs-lookup"><span data-stu-id="42cac-108">Level</span></span>|<span data-ttu-id="42cac-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="42cac-109">Verbose</span></span>|  
|<span data-ttu-id="42cac-110">通道</span><span class="sxs-lookup"><span data-stu-id="42cac-110">Channel</span></span>|<span data-ttu-id="42cac-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="42cac-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="42cac-112">描述</span><span class="sxs-lookup"><span data-stu-id="42cac-112">Description</span></span>  
 <span data-ttu-id="42cac-113">表示 FaultWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="42cac-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="42cac-114">訊息</span><span class="sxs-lookup"><span data-stu-id="42cac-114">Message</span></span>  
 <span data-ttu-id="42cac-115">開始執行的 faultworkitem 活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="42cac-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="42cac-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42cac-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="42cac-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="42cac-117">Details</span></span>  
  
|<span data-ttu-id="42cac-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="42cac-118">Data Item Name</span></span>|<span data-ttu-id="42cac-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="42cac-119">Data Item Type</span></span>|<span data-ttu-id="42cac-120">描述</span><span class="sxs-lookup"><span data-stu-id="42cac-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="42cac-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="42cac-121">FaultActivity</span></span>|<span data-ttu-id="42cac-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-122">xs:string</span></span>|<span data-ttu-id="42cac-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="42cac-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="42cac-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="42cac-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="42cac-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-125">xs:string</span></span>|<span data-ttu-id="42cac-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="42cac-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="42cac-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="42cac-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="42cac-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-128">xs:string</span></span>|<span data-ttu-id="42cac-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="42cac-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="42cac-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="42cac-130">ExceptionActivity</span></span>|<span data-ttu-id="42cac-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-131">xs:string</span></span>|<span data-ttu-id="42cac-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="42cac-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="42cac-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="42cac-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="42cac-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-134">xs:string</span></span>|<span data-ttu-id="42cac-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="42cac-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="42cac-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="42cac-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="42cac-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-137">xs:string</span></span>|<span data-ttu-id="42cac-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="42cac-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="42cac-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="42cac-139">Exception</span></span>|<span data-ttu-id="42cac-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-140">xs:string</span></span>|<span data-ttu-id="42cac-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="42cac-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="42cac-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="42cac-142">AppDomain</span></span>|<span data-ttu-id="42cac-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="42cac-143">xs:string</span></span>|<span data-ttu-id="42cac-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="42cac-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
