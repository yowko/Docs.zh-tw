---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: 557155fab35a37bdbaa45efb26d6bc025ad825c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281829"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="0016f-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="0016f-102">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="0016f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0016f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0016f-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="0016f-104">ID</span></span>|<span data-ttu-id="0016f-105">1031</span><span class="sxs-lookup"><span data-stu-id="0016f-105">1031</span></span>|  
|<span data-ttu-id="0016f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0016f-106">Keywords</span></span>|<span data-ttu-id="0016f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0016f-107">WFRuntime</span></span>|  
|<span data-ttu-id="0016f-108">層級</span><span class="sxs-lookup"><span data-stu-id="0016f-108">Level</span></span>|<span data-ttu-id="0016f-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="0016f-109">Verbose</span></span>|  
|<span data-ttu-id="0016f-110">通路</span><span class="sxs-lookup"><span data-stu-id="0016f-110">Channel</span></span>|<span data-ttu-id="0016f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0016f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0016f-112">描述</span><span class="sxs-lookup"><span data-stu-id="0016f-112">Description</span></span>  

 <span data-ttu-id="0016f-113">表示 FaultWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="0016f-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0016f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0016f-114">Message</span></span>  

 <span data-ttu-id="0016f-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="0016f-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="0016f-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0016f-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0016f-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0016f-117">Details</span></span>  
  
|<span data-ttu-id="0016f-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0016f-118">Data Item Name</span></span>|<span data-ttu-id="0016f-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0016f-119">Data Item Type</span></span>|<span data-ttu-id="0016f-120">描述</span><span class="sxs-lookup"><span data-stu-id="0016f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0016f-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="0016f-121">FaultActivity</span></span>|<span data-ttu-id="0016f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-122">xs:string</span></span>|<span data-ttu-id="0016f-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0016f-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="0016f-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0016f-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="0016f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-125">xs:string</span></span>|<span data-ttu-id="0016f-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0016f-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="0016f-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0016f-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="0016f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-128">xs:string</span></span>|<span data-ttu-id="0016f-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0016f-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="0016f-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="0016f-130">ExceptionActivity</span></span>|<span data-ttu-id="0016f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-131">xs:string</span></span>|<span data-ttu-id="0016f-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0016f-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0016f-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0016f-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="0016f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-134">xs:string</span></span>|<span data-ttu-id="0016f-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0016f-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0016f-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0016f-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="0016f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-137">xs:string</span></span>|<span data-ttu-id="0016f-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="0016f-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0016f-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="0016f-139">Exception</span></span>|<span data-ttu-id="0016f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-140">xs:string</span></span>|<span data-ttu-id="0016f-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="0016f-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="0016f-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0016f-142">AppDomain</span></span>|<span data-ttu-id="0016f-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="0016f-143">xs:string</span></span>|<span data-ttu-id="0016f-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0016f-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
