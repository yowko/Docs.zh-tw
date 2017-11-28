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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ba1ae69caff2e08da58e824d35341d3781ea8ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="e68a6-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e68a6-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e68a6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e68a6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e68a6-104">ID</span><span class="sxs-lookup"><span data-stu-id="e68a6-104">ID</span></span>|<span data-ttu-id="e68a6-105">1029</span><span class="sxs-lookup"><span data-stu-id="e68a6-105">1029</span></span>|  
|<span data-ttu-id="e68a6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e68a6-106">Keywords</span></span>|<span data-ttu-id="e68a6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e68a6-107">WFRuntime</span></span>|  
|<span data-ttu-id="e68a6-108">層級</span><span class="sxs-lookup"><span data-stu-id="e68a6-108">Level</span></span>|<span data-ttu-id="e68a6-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="e68a6-109">Verbose</span></span>|  
|<span data-ttu-id="e68a6-110">通道</span><span class="sxs-lookup"><span data-stu-id="e68a6-110">Channel</span></span>|<span data-ttu-id="e68a6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e68a6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e68a6-112">描述</span><span class="sxs-lookup"><span data-stu-id="e68a6-112">Description</span></span>  
 <span data-ttu-id="e68a6-113">表示已排定 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="e68a6-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e68a6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e68a6-114">Message</span></span>  
 <span data-ttu-id="e68a6-115">FaultWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="e68a6-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e68a6-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e68a6-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e68a6-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e68a6-117">Details</span></span>  
  
|<span data-ttu-id="e68a6-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e68a6-118">Data Item Name</span></span>|<span data-ttu-id="e68a6-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e68a6-119">Data Item Type</span></span>|<span data-ttu-id="e68a6-120">描述</span><span class="sxs-lookup"><span data-stu-id="e68a6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e68a6-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e68a6-121">FaultActivity</span></span>|<span data-ttu-id="e68a6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-122">xs:string</span></span>|<span data-ttu-id="e68a6-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e68a6-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e68a6-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e68a6-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e68a6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-125">xs:string</span></span>|<span data-ttu-id="e68a6-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e68a6-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e68a6-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e68a6-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e68a6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-128">xs:string</span></span>|<span data-ttu-id="e68a6-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="e68a6-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e68a6-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e68a6-130">ExceptionActivity</span></span>|<span data-ttu-id="e68a6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-131">xs:string</span></span>|<span data-ttu-id="e68a6-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e68a6-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e68a6-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e68a6-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e68a6-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-134">xs:string</span></span>|<span data-ttu-id="e68a6-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e68a6-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e68a6-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e68a6-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e68a6-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-137">xs:string</span></span>|<span data-ttu-id="e68a6-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="e68a6-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e68a6-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e68a6-139">Exception</span></span>|<span data-ttu-id="e68a6-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-140">xs:string</span></span>|<span data-ttu-id="e68a6-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="e68a6-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e68a6-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e68a6-142">AppDomain</span></span>|<span data-ttu-id="e68a6-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e68a6-143">xs:string</span></span>|<span data-ttu-id="e68a6-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e68a6-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
