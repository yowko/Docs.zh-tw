---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509726"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="f5adf-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="f5adf-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f5adf-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f5adf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5adf-104">ID</span><span class="sxs-lookup"><span data-stu-id="f5adf-104">ID</span></span>|<span data-ttu-id="f5adf-105">1029</span><span class="sxs-lookup"><span data-stu-id="f5adf-105">1029</span></span>|  
|<span data-ttu-id="f5adf-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f5adf-106">Keywords</span></span>|<span data-ttu-id="f5adf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f5adf-107">WFRuntime</span></span>|  
|<span data-ttu-id="f5adf-108">層級</span><span class="sxs-lookup"><span data-stu-id="f5adf-108">Level</span></span>|<span data-ttu-id="f5adf-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f5adf-109">Verbose</span></span>|  
|<span data-ttu-id="f5adf-110">通道</span><span class="sxs-lookup"><span data-stu-id="f5adf-110">Channel</span></span>|<span data-ttu-id="f5adf-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f5adf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f5adf-112">描述</span><span class="sxs-lookup"><span data-stu-id="f5adf-112">Description</span></span>  
 <span data-ttu-id="f5adf-113">表示已排定 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="f5adf-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f5adf-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f5adf-114">Message</span></span>  
 <span data-ttu-id="f5adf-115">FaultWorkItem 已排定活動 '%1'、 DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="f5adf-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="f5adf-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f5adf-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f5adf-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f5adf-117">Details</span></span>  
  
|<span data-ttu-id="f5adf-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f5adf-118">Data Item Name</span></span>|<span data-ttu-id="f5adf-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f5adf-119">Data Item Type</span></span>|<span data-ttu-id="f5adf-120">描述</span><span class="sxs-lookup"><span data-stu-id="f5adf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f5adf-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="f5adf-121">FaultActivity</span></span>|<span data-ttu-id="f5adf-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-122">xs:string</span></span>|<span data-ttu-id="f5adf-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f5adf-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="f5adf-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f5adf-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="f5adf-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-125">xs:string</span></span>|<span data-ttu-id="f5adf-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f5adf-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="f5adf-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f5adf-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="f5adf-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-128">xs:string</span></span>|<span data-ttu-id="f5adf-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f5adf-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="f5adf-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="f5adf-130">ExceptionActivity</span></span>|<span data-ttu-id="f5adf-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-131">xs:string</span></span>|<span data-ttu-id="f5adf-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="f5adf-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f5adf-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f5adf-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="f5adf-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-134">xs:string</span></span>|<span data-ttu-id="f5adf-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="f5adf-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f5adf-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f5adf-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="f5adf-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-137">xs:string</span></span>|<span data-ttu-id="f5adf-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f5adf-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f5adf-139">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f5adf-139">Exception</span></span>|<span data-ttu-id="f5adf-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-140">xs:string</span></span>|<span data-ttu-id="f5adf-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="f5adf-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="f5adf-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f5adf-142">AppDomain</span></span>|<span data-ttu-id="f5adf-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5adf-143">xs:string</span></span>|<span data-ttu-id="f5adf-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f5adf-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
