---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: 5c109607b2d353d3d4a5a693f29ab66bb76c8398
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275085"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="f8604-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="f8604-102">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="f8604-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f8604-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8604-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f8604-104">ID</span></span>|<span data-ttu-id="f8604-105">1029</span><span class="sxs-lookup"><span data-stu-id="f8604-105">1029</span></span>|  
|<span data-ttu-id="f8604-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f8604-106">Keywords</span></span>|<span data-ttu-id="f8604-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f8604-107">WFRuntime</span></span>|  
|<span data-ttu-id="f8604-108">層級</span><span class="sxs-lookup"><span data-stu-id="f8604-108">Level</span></span>|<span data-ttu-id="f8604-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="f8604-109">Verbose</span></span>|  
|<span data-ttu-id="f8604-110">通路</span><span class="sxs-lookup"><span data-stu-id="f8604-110">Channel</span></span>|<span data-ttu-id="f8604-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f8604-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f8604-112">描述</span><span class="sxs-lookup"><span data-stu-id="f8604-112">Description</span></span>  

 <span data-ttu-id="f8604-113">表示已排定 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="f8604-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f8604-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f8604-114">Message</span></span>  

 <span data-ttu-id="f8604-115">已排定活動 ' %1 '、DisplayName： ' %2 '、InstanceId： ' %3 ' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="f8604-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="f8604-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8604-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f8604-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f8604-117">Details</span></span>  
  
|<span data-ttu-id="f8604-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f8604-118">Data Item Name</span></span>|<span data-ttu-id="f8604-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f8604-119">Data Item Type</span></span>|<span data-ttu-id="f8604-120">描述</span><span class="sxs-lookup"><span data-stu-id="f8604-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f8604-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="f8604-121">FaultActivity</span></span>|<span data-ttu-id="f8604-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-122">xs:string</span></span>|<span data-ttu-id="f8604-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f8604-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="f8604-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f8604-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="f8604-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-125">xs:string</span></span>|<span data-ttu-id="f8604-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f8604-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="f8604-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f8604-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="f8604-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-128">xs:string</span></span>|<span data-ttu-id="f8604-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f8604-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="f8604-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="f8604-130">ExceptionActivity</span></span>|<span data-ttu-id="f8604-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-131">xs:string</span></span>|<span data-ttu-id="f8604-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f8604-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f8604-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f8604-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="f8604-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-134">xs:string</span></span>|<span data-ttu-id="f8604-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f8604-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f8604-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f8604-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="f8604-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-137">xs:string</span></span>|<span data-ttu-id="f8604-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f8604-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f8604-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f8604-139">Exception</span></span>|<span data-ttu-id="f8604-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-140">xs:string</span></span>|<span data-ttu-id="f8604-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="f8604-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="f8604-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f8604-142">AppDomain</span></span>|<span data-ttu-id="f8604-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8604-143">xs:string</span></span>|<span data-ttu-id="f8604-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f8604-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
