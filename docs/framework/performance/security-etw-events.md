---
title: 安全性 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046169"
---
# <a name="security-etw-events"></a><span data-ttu-id="cdbe4-102">安全性 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="cdbe4-103">強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="cdbe4-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="cdbe4-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="cdbe4-105">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="cdbe4-106">AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="cdbe4-107">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="cdbe4-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="cdbe4-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="cdbe4-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="cdbe4-110">Keyword for raising the event</span></span>|<span data-ttu-id="cdbe4-111">層級</span><span class="sxs-lookup"><span data-stu-id="cdbe4-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdbe4-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="cdbe4-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="cdbe4-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="cdbe4-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="cdbe4-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdbe4-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-115">Event</span></span>|<span data-ttu-id="cdbe4-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cdbe4-116">Event ID</span></span>|<span data-ttu-id="cdbe4-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="cdbe4-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="cdbe4-118">181</span><span class="sxs-lookup"><span data-stu-id="cdbe4-118">181</span></span>|<span data-ttu-id="cdbe4-119">強式名稱驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="cdbe4-120">182</span><span class="sxs-lookup"><span data-stu-id="cdbe4-120">182</span></span>|<span data-ttu-id="cdbe4-121">強式名稱驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="cdbe4-122">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdbe4-123">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="cdbe4-123">Field name</span></span>|<span data-ttu-id="cdbe4-124">資料類型</span><span class="sxs-lookup"><span data-stu-id="cdbe4-124">Data type</span></span>|<span data-ttu-id="cdbe4-125">描述</span><span class="sxs-lookup"><span data-stu-id="cdbe4-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdbe4-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="cdbe4-126">VerificationFlags</span></span>|<span data-ttu-id="cdbe4-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cdbe4-127">win:UInt32</span></span>|<span data-ttu-id="cdbe4-128">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-128">The verification flags.</span></span>|  
|<span data-ttu-id="cdbe4-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="cdbe4-129">ErrorCode</span></span>|<span data-ttu-id="cdbe4-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cdbe4-130">win:UInt32</span></span>|<span data-ttu-id="cdbe4-131">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-131">The HResult error code.</span></span>|  
|<span data-ttu-id="cdbe4-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="cdbe4-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="cdbe4-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="cdbe4-133">win:UnicodeString</span></span>|<span data-ttu-id="cdbe4-134">完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="cdbe4-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdbe4-135">ClrInstanceID</span></span>|<span data-ttu-id="cdbe4-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cdbe4-136">win:UInt16</span></span>|<span data-ttu-id="cdbe4-137">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="cdbe4-138">回到頁首</span><span class="sxs-lookup"><span data-stu-id="cdbe4-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="cdbe4-139">AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="cdbe4-140">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="cdbe4-141">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="cdbe4-141">Keyword for raising the event</span></span>|<span data-ttu-id="cdbe4-142">層級</span><span class="sxs-lookup"><span data-stu-id="cdbe4-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cdbe4-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="cdbe4-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="cdbe4-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="cdbe4-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="cdbe4-145">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cdbe4-146">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-146">Event</span></span>|<span data-ttu-id="cdbe4-147">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cdbe4-147">Event ID</span></span>|<span data-ttu-id="cdbe4-148">引發的時機</span><span class="sxs-lookup"><span data-stu-id="cdbe4-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="cdbe4-149">183</span><span class="sxs-lookup"><span data-stu-id="cdbe4-149">183</span></span>|<span data-ttu-id="cdbe4-150">Authenticode 驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="cdbe4-151">184</span><span class="sxs-lookup"><span data-stu-id="cdbe4-151">184</span></span>|<span data-ttu-id="cdbe4-152">Authenticode 驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="cdbe4-153">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cdbe4-154">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="cdbe4-154">Field name</span></span>|<span data-ttu-id="cdbe4-155">資料類型</span><span class="sxs-lookup"><span data-stu-id="cdbe4-155">Data type</span></span>|<span data-ttu-id="cdbe4-156">描述</span><span class="sxs-lookup"><span data-stu-id="cdbe4-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cdbe4-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="cdbe4-157">VerificationFlags</span></span>|<span data-ttu-id="cdbe4-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cdbe4-158">win:UInt32</span></span>|<span data-ttu-id="cdbe4-159">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-159">The verification flags.</span></span>|  
|<span data-ttu-id="cdbe4-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="cdbe4-160">ErrorCode</span></span>|<span data-ttu-id="cdbe4-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="cdbe4-161">win:UInt32</span></span>|<span data-ttu-id="cdbe4-162">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-162">The HResult error code.</span></span>|  
|<span data-ttu-id="cdbe4-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="cdbe4-163">ModulePath</span></span>|<span data-ttu-id="cdbe4-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="cdbe4-164">win:UnicodeString</span></span>|<span data-ttu-id="cdbe4-165">模組路徑。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-165">The module path.</span></span>|  
|<span data-ttu-id="cdbe4-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cdbe4-166">ClrInstanceID</span></span>|<span data-ttu-id="cdbe4-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="cdbe4-167">win:UInt16</span></span>|<span data-ttu-id="cdbe4-168">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="cdbe4-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdbe4-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdbe4-169">See also</span></span>

- [<span data-ttu-id="cdbe4-170">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="cdbe4-170">CLR ETW Events</span></span>](clr-etw-events.md)
