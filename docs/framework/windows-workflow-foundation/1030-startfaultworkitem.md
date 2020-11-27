---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 52034f7cc7c6f6749fbbbf06db9267ecb6279ee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281855"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="62c24-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="62c24-102">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="62c24-103">屬性</span><span class="sxs-lookup"><span data-stu-id="62c24-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62c24-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="62c24-104">ID</span></span>|<span data-ttu-id="62c24-105">1030</span><span class="sxs-lookup"><span data-stu-id="62c24-105">1030</span></span>|  
|<span data-ttu-id="62c24-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="62c24-106">Keywords</span></span>|<span data-ttu-id="62c24-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="62c24-107">WFRuntime</span></span>|  
|<span data-ttu-id="62c24-108">層級</span><span class="sxs-lookup"><span data-stu-id="62c24-108">Level</span></span>|<span data-ttu-id="62c24-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="62c24-109">Verbose</span></span>|  
|<span data-ttu-id="62c24-110">通路</span><span class="sxs-lookup"><span data-stu-id="62c24-110">Channel</span></span>|<span data-ttu-id="62c24-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="62c24-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="62c24-112">描述</span><span class="sxs-lookup"><span data-stu-id="62c24-112">Description</span></span>  

 <span data-ttu-id="62c24-113">表示 FaultWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="62c24-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="62c24-114">訊息</span><span class="sxs-lookup"><span data-stu-id="62c24-114">Message</span></span>  

 <span data-ttu-id="62c24-115">開始執行活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="62c24-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="62c24-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62c24-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="62c24-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="62c24-117">Details</span></span>  
  
|<span data-ttu-id="62c24-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="62c24-118">Data Item Name</span></span>|<span data-ttu-id="62c24-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="62c24-119">Data Item Type</span></span>|<span data-ttu-id="62c24-120">描述</span><span class="sxs-lookup"><span data-stu-id="62c24-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="62c24-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="62c24-121">FaultActivity</span></span>|<span data-ttu-id="62c24-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-122">xs:string</span></span>|<span data-ttu-id="62c24-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="62c24-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="62c24-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="62c24-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="62c24-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-125">xs:string</span></span>|<span data-ttu-id="62c24-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="62c24-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="62c24-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="62c24-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="62c24-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-128">xs:string</span></span>|<span data-ttu-id="62c24-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="62c24-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="62c24-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="62c24-130">ExceptionActivity</span></span>|<span data-ttu-id="62c24-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-131">xs:string</span></span>|<span data-ttu-id="62c24-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="62c24-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="62c24-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="62c24-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="62c24-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-134">xs:string</span></span>|<span data-ttu-id="62c24-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="62c24-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="62c24-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="62c24-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="62c24-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-137">xs:string</span></span>|<span data-ttu-id="62c24-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="62c24-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="62c24-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="62c24-139">Exception</span></span>|<span data-ttu-id="62c24-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-140">xs:string</span></span>|<span data-ttu-id="62c24-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="62c24-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="62c24-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="62c24-142">AppDomain</span></span>|<span data-ttu-id="62c24-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="62c24-143">xs:string</span></span>|<span data-ttu-id="62c24-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="62c24-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
