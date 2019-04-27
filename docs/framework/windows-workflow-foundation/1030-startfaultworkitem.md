---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924315"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="795bf-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="795bf-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="795bf-103">屬性</span><span class="sxs-lookup"><span data-stu-id="795bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="795bf-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="795bf-104">ID</span></span>|<span data-ttu-id="795bf-105">1030</span><span class="sxs-lookup"><span data-stu-id="795bf-105">1030</span></span>|  
|<span data-ttu-id="795bf-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="795bf-106">Keywords</span></span>|<span data-ttu-id="795bf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="795bf-107">WFRuntime</span></span>|  
|<span data-ttu-id="795bf-108">層級</span><span class="sxs-lookup"><span data-stu-id="795bf-108">Level</span></span>|<span data-ttu-id="795bf-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="795bf-109">Verbose</span></span>|  
|<span data-ttu-id="795bf-110">通道</span><span class="sxs-lookup"><span data-stu-id="795bf-110">Channel</span></span>|<span data-ttu-id="795bf-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="795bf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="795bf-112">描述</span><span class="sxs-lookup"><span data-stu-id="795bf-112">Description</span></span>  
 <span data-ttu-id="795bf-113">表示 FaultWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="795bf-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="795bf-114">訊息</span><span class="sxs-lookup"><span data-stu-id="795bf-114">Message</span></span>  
 <span data-ttu-id="795bf-115">開始執行活動 '%1'，DisplayName FaultWorkItem: '%2'、 InstanceId: '%3'。</span><span class="sxs-lookup"><span data-stu-id="795bf-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="795bf-116">活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="795bf-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="795bf-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="795bf-117">Details</span></span>  
  
|<span data-ttu-id="795bf-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="795bf-118">Data Item Name</span></span>|<span data-ttu-id="795bf-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="795bf-119">Data Item Type</span></span>|<span data-ttu-id="795bf-120">描述</span><span class="sxs-lookup"><span data-stu-id="795bf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="795bf-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="795bf-121">FaultActivity</span></span>|<span data-ttu-id="795bf-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-122">xs:string</span></span>|<span data-ttu-id="795bf-123">錯誤活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="795bf-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="795bf-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="795bf-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="795bf-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-125">xs:string</span></span>|<span data-ttu-id="795bf-126">錯誤活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="795bf-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="795bf-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="795bf-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="795bf-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-128">xs:string</span></span>|<span data-ttu-id="795bf-129">錯誤活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="795bf-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="795bf-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="795bf-130">ExceptionActivity</span></span>|<span data-ttu-id="795bf-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-131">xs:string</span></span>|<span data-ttu-id="795bf-132">擲回例外狀況之活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="795bf-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="795bf-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="795bf-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="795bf-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-134">xs:string</span></span>|<span data-ttu-id="795bf-135">擲回例外狀況之活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="795bf-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="795bf-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="795bf-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="795bf-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-137">xs:string</span></span>|<span data-ttu-id="795bf-138">擲回例外狀況之活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="795bf-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="795bf-139">例外</span><span class="sxs-lookup"><span data-stu-id="795bf-139">Exception</span></span>|<span data-ttu-id="795bf-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-140">xs:string</span></span>|<span data-ttu-id="795bf-141">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="795bf-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="795bf-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="795bf-142">AppDomain</span></span>|<span data-ttu-id="795bf-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="795bf-143">xs:string</span></span>|<span data-ttu-id="795bf-144">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="795bf-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
