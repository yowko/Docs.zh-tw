---
title: 安全性 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e02274b63ddf7df42d26621791de0286df9655b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395508"
---
# <a name="security-etw-events"></a><span data-ttu-id="7e22a-102">安全性 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="7e22a-103">強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。</span><span class="sxs-lookup"><span data-stu-id="7e22a-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="7e22a-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="7e22a-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="7e22a-105">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="7e22a-106">AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="7e22a-107">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="7e22a-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="7e22a-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="7e22a-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="7e22a-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="7e22a-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e22a-110">Keyword for raising the event</span></span>|<span data-ttu-id="7e22a-111">層級</span><span class="sxs-lookup"><span data-stu-id="7e22a-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7e22a-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="7e22a-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="7e22a-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7e22a-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="7e22a-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="7e22a-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7e22a-115">事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-115">Event</span></span>|<span data-ttu-id="7e22a-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7e22a-116">Event ID</span></span>|<span data-ttu-id="7e22a-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="7e22a-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="7e22a-118">181</span><span class="sxs-lookup"><span data-stu-id="7e22a-118">181</span></span>|<span data-ttu-id="7e22a-119">強式名稱驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="7e22a-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="7e22a-120">182</span><span class="sxs-lookup"><span data-stu-id="7e22a-120">182</span></span>|<span data-ttu-id="7e22a-121">強式名稱驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="7e22a-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="7e22a-122">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="7e22a-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7e22a-123">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="7e22a-123">Field name</span></span>|<span data-ttu-id="7e22a-124">資料類型</span><span class="sxs-lookup"><span data-stu-id="7e22a-124">Data type</span></span>|<span data-ttu-id="7e22a-125">描述</span><span class="sxs-lookup"><span data-stu-id="7e22a-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7e22a-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="7e22a-126">VerificationFlags</span></span>|<span data-ttu-id="7e22a-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7e22a-127">win:UInt32</span></span>|<span data-ttu-id="7e22a-128">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="7e22a-128">The verification flags.</span></span>|  
|<span data-ttu-id="7e22a-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="7e22a-129">ErrorCode</span></span>|<span data-ttu-id="7e22a-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7e22a-130">win:UInt32</span></span>|<span data-ttu-id="7e22a-131">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7e22a-131">The HResult error code.</span></span>|  
|<span data-ttu-id="7e22a-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="7e22a-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="7e22a-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7e22a-133">win:UnicodeString</span></span>|<span data-ttu-id="7e22a-134">完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="7e22a-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="7e22a-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7e22a-135">ClrInstanceID</span></span>|<span data-ttu-id="7e22a-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7e22a-136">win:UInt16</span></span>|<span data-ttu-id="7e22a-137">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="7e22a-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7e22a-138">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7e22a-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="7e22a-139">AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="7e22a-140">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="7e22a-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7e22a-141">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e22a-141">Keyword for raising the event</span></span>|<span data-ttu-id="7e22a-142">層級</span><span class="sxs-lookup"><span data-stu-id="7e22a-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7e22a-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="7e22a-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="7e22a-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7e22a-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="7e22a-145">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="7e22a-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7e22a-146">事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-146">Event</span></span>|<span data-ttu-id="7e22a-147">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7e22a-147">Event ID</span></span>|<span data-ttu-id="7e22a-148">引發的時機</span><span class="sxs-lookup"><span data-stu-id="7e22a-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="7e22a-149">183</span><span class="sxs-lookup"><span data-stu-id="7e22a-149">183</span></span>|<span data-ttu-id="7e22a-150">Authenticode 驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="7e22a-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="7e22a-151">184</span><span class="sxs-lookup"><span data-stu-id="7e22a-151">184</span></span>|<span data-ttu-id="7e22a-152">Authenticode 驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="7e22a-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="7e22a-153">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="7e22a-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7e22a-154">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="7e22a-154">Field name</span></span>|<span data-ttu-id="7e22a-155">資料類型</span><span class="sxs-lookup"><span data-stu-id="7e22a-155">Data type</span></span>|<span data-ttu-id="7e22a-156">描述</span><span class="sxs-lookup"><span data-stu-id="7e22a-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7e22a-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="7e22a-157">VerificationFlags</span></span>|<span data-ttu-id="7e22a-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7e22a-158">win:UInt32</span></span>|<span data-ttu-id="7e22a-159">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="7e22a-159">The verification flags.</span></span>|  
|<span data-ttu-id="7e22a-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="7e22a-160">ErrorCode</span></span>|<span data-ttu-id="7e22a-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7e22a-161">win:UInt32</span></span>|<span data-ttu-id="7e22a-162">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7e22a-162">The HResult error code.</span></span>|  
|<span data-ttu-id="7e22a-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="7e22a-163">ModulePath</span></span>|<span data-ttu-id="7e22a-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7e22a-164">win:UnicodeString</span></span>|<span data-ttu-id="7e22a-165">模組路徑。</span><span class="sxs-lookup"><span data-stu-id="7e22a-165">The module path.</span></span>|  
|<span data-ttu-id="7e22a-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7e22a-166">ClrInstanceID</span></span>|<span data-ttu-id="7e22a-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7e22a-167">win:UInt16</span></span>|<span data-ttu-id="7e22a-168">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="7e22a-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e22a-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e22a-169">See Also</span></span>  
 [<span data-ttu-id="7e22a-170">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="7e22a-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
