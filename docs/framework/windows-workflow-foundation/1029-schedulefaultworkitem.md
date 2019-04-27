---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924354"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="b0f44-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="b0f44-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b0f44-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b0f44-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b0f44-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="b0f44-104">ID</span></span>|<span data-ttu-id="b0f44-105">1029</span><span class="sxs-lookup"><span data-stu-id="b0f44-105">1029</span></span>|  
|<span data-ttu-id="b0f44-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b0f44-106">Keywords</span></span>|<span data-ttu-id="b0f44-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b0f44-107">WFRuntime</span></span>|  
|<span data-ttu-id="b0f44-108">層級</span><span class="sxs-lookup"><span data-stu-id="b0f44-108">Level</span></span>|<span data-ttu-id="b0f44-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b0f44-109">Verbose</span></span>|  
|<span data-ttu-id="b0f44-110">通道</span><span class="sxs-lookup"><span data-stu-id="b0f44-110">Channel</span></span>|<span data-ttu-id="b0f44-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b0f44-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b0f44-112">描述</span><span class="sxs-lookup"><span data-stu-id="b0f44-112">Description</span></span>  
 <span data-ttu-id="b0f44-113">表示已排定 FaultWorkItem。</span><span class="sxs-lookup"><span data-stu-id="b0f44-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b0f44-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b0f44-114">Message</span></span>  
 <span data-ttu-id="b0f44-115">FaultWorkItem 已排定活動 '%1'，DisplayName: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="b0f44-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="b0f44-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0f44-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b0f44-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b0f44-117">Details</span></span>  
  
|<span data-ttu-id="b0f44-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b0f44-118">Data Item Name</span></span>|<span data-ttu-id="b0f44-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b0f44-119">Data Item Type</span></span>|<span data-ttu-id="b0f44-120">描述</span><span class="sxs-lookup"><span data-stu-id="b0f44-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b0f44-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="b0f44-121">FaultActivity</span></span>|<span data-ttu-id="b0f44-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-122">xs:string</span></span>|<span data-ttu-id="b0f44-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b0f44-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="b0f44-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b0f44-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="b0f44-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-125">xs:string</span></span>|<span data-ttu-id="b0f44-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b0f44-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="b0f44-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b0f44-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="b0f44-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-128">xs:string</span></span>|<span data-ttu-id="b0f44-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="b0f44-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="b0f44-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="b0f44-130">ExceptionActivity</span></span>|<span data-ttu-id="b0f44-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-131">xs:string</span></span>|<span data-ttu-id="b0f44-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b0f44-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b0f44-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b0f44-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="b0f44-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-134">xs:string</span></span>|<span data-ttu-id="b0f44-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b0f44-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b0f44-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b0f44-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="b0f44-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-137">xs:string</span></span>|<span data-ttu-id="b0f44-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="b0f44-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b0f44-139">例外</span><span class="sxs-lookup"><span data-stu-id="b0f44-139">Exception</span></span>|<span data-ttu-id="b0f44-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-140">xs:string</span></span>|<span data-ttu-id="b0f44-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="b0f44-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="b0f44-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b0f44-142">AppDomain</span></span>|<span data-ttu-id="b0f44-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0f44-143">xs:string</span></span>|<span data-ttu-id="b0f44-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b0f44-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
