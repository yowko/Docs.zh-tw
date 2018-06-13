---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509739"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="31654-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="31654-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="31654-103">屬性</span><span class="sxs-lookup"><span data-stu-id="31654-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31654-104">ID</span><span class="sxs-lookup"><span data-stu-id="31654-104">ID</span></span>|<span data-ttu-id="31654-105">1031</span><span class="sxs-lookup"><span data-stu-id="31654-105">1031</span></span>|  
|<span data-ttu-id="31654-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="31654-106">Keywords</span></span>|<span data-ttu-id="31654-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31654-107">WFRuntime</span></span>|  
|<span data-ttu-id="31654-108">層級</span><span class="sxs-lookup"><span data-stu-id="31654-108">Level</span></span>|<span data-ttu-id="31654-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="31654-109">Verbose</span></span>|  
|<span data-ttu-id="31654-110">通道</span><span class="sxs-lookup"><span data-stu-id="31654-110">Channel</span></span>|<span data-ttu-id="31654-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="31654-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31654-112">描述</span><span class="sxs-lookup"><span data-stu-id="31654-112">Description</span></span>  
 <span data-ttu-id="31654-113">表示 FaultWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="31654-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31654-114">訊息</span><span class="sxs-lookup"><span data-stu-id="31654-114">Message</span></span>  
 <span data-ttu-id="31654-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="31654-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="31654-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="31654-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31654-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31654-117">Details</span></span>  
  
|<span data-ttu-id="31654-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="31654-118">Data Item Name</span></span>|<span data-ttu-id="31654-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="31654-119">Data Item Type</span></span>|<span data-ttu-id="31654-120">描述</span><span class="sxs-lookup"><span data-stu-id="31654-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31654-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="31654-121">FaultActivity</span></span>|<span data-ttu-id="31654-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-122">xs:string</span></span>|<span data-ttu-id="31654-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="31654-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="31654-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="31654-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="31654-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-125">xs:string</span></span>|<span data-ttu-id="31654-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="31654-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="31654-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="31654-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="31654-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-128">xs:string</span></span>|<span data-ttu-id="31654-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="31654-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="31654-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="31654-130">ExceptionActivity</span></span>|<span data-ttu-id="31654-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-131">xs:string</span></span>|<span data-ttu-id="31654-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="31654-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="31654-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="31654-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="31654-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-134">xs:string</span></span>|<span data-ttu-id="31654-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="31654-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="31654-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="31654-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="31654-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-137">xs:string</span></span>|<span data-ttu-id="31654-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="31654-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="31654-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="31654-139">Exception</span></span>|<span data-ttu-id="31654-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-140">xs:string</span></span>|<span data-ttu-id="31654-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="31654-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="31654-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31654-142">AppDomain</span></span>|<span data-ttu-id="31654-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="31654-143">xs:string</span></span>|<span data-ttu-id="31654-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="31654-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
