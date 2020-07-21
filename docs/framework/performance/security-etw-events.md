---
title: 安全性 ETW 事件
description: 瞭解安全性 ETW 事件，這會在 .NET 中的強式名稱驗證和 Authenticode 驗證期間引發。
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474211"
---
# <a name="security-etw-events"></a><span data-ttu-id="be5d7-103">安全性 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="be5d7-103">Security ETW Events</span></span>

<span data-ttu-id="be5d7-104">強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。</span><span class="sxs-lookup"><span data-stu-id="be5d7-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="be5d7-105">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="be5d7-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="be5d7-106">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="be5d7-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="be5d7-107">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="be5d7-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="be5d7-108">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="be5d7-108">Keyword for raising the event</span></span>|<span data-ttu-id="be5d7-109">層級</span><span class="sxs-lookup"><span data-stu-id="be5d7-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="be5d7-110">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="be5d7-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="be5d7-111">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="be5d7-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="be5d7-112">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="be5d7-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="be5d7-113">事件</span><span class="sxs-lookup"><span data-stu-id="be5d7-113">Event</span></span>|<span data-ttu-id="be5d7-114">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="be5d7-114">Event ID</span></span>|<span data-ttu-id="be5d7-115">引發的時機</span><span class="sxs-lookup"><span data-stu-id="be5d7-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="be5d7-116">181</span><span class="sxs-lookup"><span data-stu-id="be5d7-116">181</span></span>|<span data-ttu-id="be5d7-117">強式名稱驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="be5d7-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="be5d7-118">182</span><span class="sxs-lookup"><span data-stu-id="be5d7-118">182</span></span>|<span data-ttu-id="be5d7-119">強式名稱驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="be5d7-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="be5d7-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="be5d7-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="be5d7-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="be5d7-121">Field name</span></span>|<span data-ttu-id="be5d7-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="be5d7-122">Data type</span></span>|<span data-ttu-id="be5d7-123">描述</span><span class="sxs-lookup"><span data-stu-id="be5d7-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="be5d7-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="be5d7-124">VerificationFlags</span></span>|<span data-ttu-id="be5d7-125">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="be5d7-125">win:UInt32</span></span>|<span data-ttu-id="be5d7-126">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="be5d7-126">The verification flags.</span></span>|  
|<span data-ttu-id="be5d7-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="be5d7-127">ErrorCode</span></span>|<span data-ttu-id="be5d7-128">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="be5d7-128">win:UInt32</span></span>|<span data-ttu-id="be5d7-129">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="be5d7-129">The HResult error code.</span></span>|  
|<span data-ttu-id="be5d7-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="be5d7-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="be5d7-131">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="be5d7-131">win:UnicodeString</span></span>|<span data-ttu-id="be5d7-132">完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="be5d7-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="be5d7-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="be5d7-133">ClrInstanceID</span></span>|<span data-ttu-id="be5d7-134">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="be5d7-134">win:UInt16</span></span>|<span data-ttu-id="be5d7-135">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="be5d7-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="be5d7-136">AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="be5d7-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="be5d7-137">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="be5d7-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="be5d7-138">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="be5d7-138">Keyword for raising the event</span></span>|<span data-ttu-id="be5d7-139">層級</span><span class="sxs-lookup"><span data-stu-id="be5d7-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="be5d7-140">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="be5d7-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="be5d7-141">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="be5d7-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="be5d7-142">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="be5d7-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="be5d7-143">事件</span><span class="sxs-lookup"><span data-stu-id="be5d7-143">Event</span></span>|<span data-ttu-id="be5d7-144">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="be5d7-144">Event ID</span></span>|<span data-ttu-id="be5d7-145">引發的時機</span><span class="sxs-lookup"><span data-stu-id="be5d7-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="be5d7-146">183</span><span class="sxs-lookup"><span data-stu-id="be5d7-146">183</span></span>|<span data-ttu-id="be5d7-147">Authenticode 驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="be5d7-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="be5d7-148">184</span><span class="sxs-lookup"><span data-stu-id="be5d7-148">184</span></span>|<span data-ttu-id="be5d7-149">Authenticode 驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="be5d7-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="be5d7-150">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="be5d7-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="be5d7-151">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="be5d7-151">Field name</span></span>|<span data-ttu-id="be5d7-152">資料類型</span><span class="sxs-lookup"><span data-stu-id="be5d7-152">Data type</span></span>|<span data-ttu-id="be5d7-153">描述</span><span class="sxs-lookup"><span data-stu-id="be5d7-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="be5d7-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="be5d7-154">VerificationFlags</span></span>|<span data-ttu-id="be5d7-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="be5d7-155">win:UInt32</span></span>|<span data-ttu-id="be5d7-156">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="be5d7-156">The verification flags.</span></span>|  
|<span data-ttu-id="be5d7-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="be5d7-157">ErrorCode</span></span>|<span data-ttu-id="be5d7-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="be5d7-158">win:UInt32</span></span>|<span data-ttu-id="be5d7-159">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="be5d7-159">The HResult error code.</span></span>|  
|<span data-ttu-id="be5d7-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="be5d7-160">ModulePath</span></span>|<span data-ttu-id="be5d7-161">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="be5d7-161">win:UnicodeString</span></span>|<span data-ttu-id="be5d7-162">模組路徑。</span><span class="sxs-lookup"><span data-stu-id="be5d7-162">The module path.</span></span>|  
|<span data-ttu-id="be5d7-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="be5d7-163">ClrInstanceID</span></span>|<span data-ttu-id="be5d7-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="be5d7-164">win:UInt16</span></span>|<span data-ttu-id="be5d7-165">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="be5d7-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be5d7-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be5d7-166">See also</span></span>

- [<span data-ttu-id="be5d7-167">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="be5d7-167">CLR ETW Events</span></span>](clr-etw-events.md)
