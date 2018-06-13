---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509676"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="07839-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="07839-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="07839-103">屬性</span><span class="sxs-lookup"><span data-stu-id="07839-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07839-104">ID</span><span class="sxs-lookup"><span data-stu-id="07839-104">ID</span></span>|<span data-ttu-id="07839-105">1030</span><span class="sxs-lookup"><span data-stu-id="07839-105">1030</span></span>|  
|<span data-ttu-id="07839-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="07839-106">Keywords</span></span>|<span data-ttu-id="07839-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="07839-107">WFRuntime</span></span>|  
|<span data-ttu-id="07839-108">層級</span><span class="sxs-lookup"><span data-stu-id="07839-108">Level</span></span>|<span data-ttu-id="07839-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="07839-109">Verbose</span></span>|  
|<span data-ttu-id="07839-110">通道</span><span class="sxs-lookup"><span data-stu-id="07839-110">Channel</span></span>|<span data-ttu-id="07839-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="07839-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="07839-112">描述</span><span class="sxs-lookup"><span data-stu-id="07839-112">Description</span></span>  
 <span data-ttu-id="07839-113">表示 FaultWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="07839-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="07839-114">訊息</span><span class="sxs-lookup"><span data-stu-id="07839-114">Message</span></span>  
 <span data-ttu-id="07839-115">開始執行的 faultworkitem 活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="07839-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="07839-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="07839-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="07839-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="07839-117">Details</span></span>  
  
|<span data-ttu-id="07839-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="07839-118">Data Item Name</span></span>|<span data-ttu-id="07839-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="07839-119">Data Item Type</span></span>|<span data-ttu-id="07839-120">描述</span><span class="sxs-lookup"><span data-stu-id="07839-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="07839-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="07839-121">FaultActivity</span></span>|<span data-ttu-id="07839-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-122">xs:string</span></span>|<span data-ttu-id="07839-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="07839-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="07839-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="07839-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="07839-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-125">xs:string</span></span>|<span data-ttu-id="07839-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="07839-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="07839-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="07839-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="07839-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-128">xs:string</span></span>|<span data-ttu-id="07839-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="07839-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="07839-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="07839-130">ExceptionActivity</span></span>|<span data-ttu-id="07839-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-131">xs:string</span></span>|<span data-ttu-id="07839-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="07839-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="07839-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="07839-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="07839-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-134">xs:string</span></span>|<span data-ttu-id="07839-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="07839-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="07839-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="07839-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="07839-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-137">xs:string</span></span>|<span data-ttu-id="07839-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="07839-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="07839-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="07839-139">Exception</span></span>|<span data-ttu-id="07839-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-140">xs:string</span></span>|<span data-ttu-id="07839-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="07839-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="07839-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="07839-142">AppDomain</span></span>|<span data-ttu-id="07839-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="07839-143">xs:string</span></span>|<span data-ttu-id="07839-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="07839-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
