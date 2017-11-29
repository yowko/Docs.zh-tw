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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 260647b56d945600afea5609f06d36385fa66014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="337ed-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="337ed-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="337ed-103">屬性</span><span class="sxs-lookup"><span data-stu-id="337ed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="337ed-104">ID</span><span class="sxs-lookup"><span data-stu-id="337ed-104">ID</span></span>|<span data-ttu-id="337ed-105">1031</span><span class="sxs-lookup"><span data-stu-id="337ed-105">1031</span></span>|  
|<span data-ttu-id="337ed-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="337ed-106">Keywords</span></span>|<span data-ttu-id="337ed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="337ed-107">WFRuntime</span></span>|  
|<span data-ttu-id="337ed-108">層級</span><span class="sxs-lookup"><span data-stu-id="337ed-108">Level</span></span>|<span data-ttu-id="337ed-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="337ed-109">Verbose</span></span>|  
|<span data-ttu-id="337ed-110">通道</span><span class="sxs-lookup"><span data-stu-id="337ed-110">Channel</span></span>|<span data-ttu-id="337ed-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="337ed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="337ed-112">描述</span><span class="sxs-lookup"><span data-stu-id="337ed-112">Description</span></span>  
 <span data-ttu-id="337ed-113">表示 FaultWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="337ed-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="337ed-114">訊息</span><span class="sxs-lookup"><span data-stu-id="337ed-114">Message</span></span>  
 <span data-ttu-id="337ed-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="337ed-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="337ed-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="337ed-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="337ed-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="337ed-117">Details</span></span>  
  
|<span data-ttu-id="337ed-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="337ed-118">Data Item Name</span></span>|<span data-ttu-id="337ed-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="337ed-119">Data Item Type</span></span>|<span data-ttu-id="337ed-120">描述</span><span class="sxs-lookup"><span data-stu-id="337ed-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="337ed-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="337ed-121">FaultActivity</span></span>|<span data-ttu-id="337ed-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-122">xs:string</span></span>|<span data-ttu-id="337ed-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="337ed-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="337ed-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="337ed-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="337ed-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-125">xs:string</span></span>|<span data-ttu-id="337ed-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="337ed-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="337ed-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="337ed-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="337ed-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-128">xs:string</span></span>|<span data-ttu-id="337ed-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="337ed-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="337ed-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="337ed-130">ExceptionActivity</span></span>|<span data-ttu-id="337ed-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-131">xs:string</span></span>|<span data-ttu-id="337ed-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="337ed-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="337ed-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="337ed-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="337ed-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-134">xs:string</span></span>|<span data-ttu-id="337ed-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="337ed-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="337ed-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="337ed-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="337ed-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-137">xs:string</span></span>|<span data-ttu-id="337ed-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="337ed-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="337ed-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="337ed-139">Exception</span></span>|<span data-ttu-id="337ed-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-140">xs:string</span></span>|<span data-ttu-id="337ed-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="337ed-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="337ed-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="337ed-142">AppDomain</span></span>|<span data-ttu-id="337ed-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="337ed-143">xs:string</span></span>|<span data-ttu-id="337ed-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="337ed-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
