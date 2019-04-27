---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008794"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="8c02c-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="8c02c-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8c02c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8c02c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c02c-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="8c02c-104">ID</span></span>|<span data-ttu-id="8c02c-105">1031</span><span class="sxs-lookup"><span data-stu-id="8c02c-105">1031</span></span>|  
|<span data-ttu-id="8c02c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8c02c-106">Keywords</span></span>|<span data-ttu-id="8c02c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8c02c-107">WFRuntime</span></span>|  
|<span data-ttu-id="8c02c-108">層級</span><span class="sxs-lookup"><span data-stu-id="8c02c-108">Level</span></span>|<span data-ttu-id="8c02c-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8c02c-109">Verbose</span></span>|  
|<span data-ttu-id="8c02c-110">通道</span><span class="sxs-lookup"><span data-stu-id="8c02c-110">Channel</span></span>|<span data-ttu-id="8c02c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8c02c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c02c-112">描述</span><span class="sxs-lookup"><span data-stu-id="8c02c-112">Description</span></span>  
 <span data-ttu-id="8c02c-113">表示 FaultWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="8c02c-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c02c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8c02c-114">Message</span></span>  
 <span data-ttu-id="8c02c-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="8c02c-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="8c02c-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8c02c-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c02c-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c02c-117">Details</span></span>  
  
|<span data-ttu-id="8c02c-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8c02c-118">Data Item Name</span></span>|<span data-ttu-id="8c02c-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8c02c-119">Data Item Type</span></span>|<span data-ttu-id="8c02c-120">描述</span><span class="sxs-lookup"><span data-stu-id="8c02c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c02c-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="8c02c-121">FaultActivity</span></span>|<span data-ttu-id="8c02c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-122">xs:string</span></span>|<span data-ttu-id="8c02c-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8c02c-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="8c02c-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c02c-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="8c02c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-125">xs:string</span></span>|<span data-ttu-id="8c02c-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8c02c-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="8c02c-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8c02c-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="8c02c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-128">xs:string</span></span>|<span data-ttu-id="8c02c-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="8c02c-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="8c02c-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="8c02c-130">ExceptionActivity</span></span>|<span data-ttu-id="8c02c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-131">xs:string</span></span>|<span data-ttu-id="8c02c-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8c02c-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8c02c-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c02c-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="8c02c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-134">xs:string</span></span>|<span data-ttu-id="8c02c-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8c02c-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8c02c-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8c02c-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="8c02c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-137">xs:string</span></span>|<span data-ttu-id="8c02c-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="8c02c-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8c02c-139">例外</span><span class="sxs-lookup"><span data-stu-id="8c02c-139">Exception</span></span>|<span data-ttu-id="8c02c-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-140">xs:string</span></span>|<span data-ttu-id="8c02c-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c02c-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="8c02c-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c02c-142">AppDomain</span></span>|<span data-ttu-id="8c02c-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c02c-143">xs:string</span></span>|<span data-ttu-id="8c02c-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8c02c-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
