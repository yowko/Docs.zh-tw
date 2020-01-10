---
title: 安全性 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: c443bda8cdc2c6b32760e9dcba8b81a29d81660b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715945"
---
# <a name="security-etw-events"></a><span data-ttu-id="2280f-102">安全性 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="2280f-102">Security ETW Events</span></span>

<span data-ttu-id="2280f-103">強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。</span><span class="sxs-lookup"><span data-stu-id="2280f-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="2280f-104">StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="2280f-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="2280f-105">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="2280f-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="2280f-106">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="2280f-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2280f-107">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2280f-107">Keyword for raising the event</span></span>|<span data-ttu-id="2280f-108">Level</span><span class="sxs-lookup"><span data-stu-id="2280f-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2280f-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="2280f-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="2280f-110">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="2280f-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="2280f-111">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2280f-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2280f-112">Event</span><span class="sxs-lookup"><span data-stu-id="2280f-112">Event</span></span>|<span data-ttu-id="2280f-113">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2280f-113">Event ID</span></span>|<span data-ttu-id="2280f-114">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2280f-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="2280f-115">181</span><span class="sxs-lookup"><span data-stu-id="2280f-115">181</span></span>|<span data-ttu-id="2280f-116">強式名稱驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="2280f-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="2280f-117">182</span><span class="sxs-lookup"><span data-stu-id="2280f-117">182</span></span>|<span data-ttu-id="2280f-118">強式名稱驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="2280f-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="2280f-119">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="2280f-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2280f-120">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="2280f-120">Field name</span></span>|<span data-ttu-id="2280f-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="2280f-121">Data type</span></span>|<span data-ttu-id="2280f-122">描述</span><span class="sxs-lookup"><span data-stu-id="2280f-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2280f-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="2280f-123">VerificationFlags</span></span>|<span data-ttu-id="2280f-124">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2280f-124">win:UInt32</span></span>|<span data-ttu-id="2280f-125">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="2280f-125">The verification flags.</span></span>|  
|<span data-ttu-id="2280f-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="2280f-126">ErrorCode</span></span>|<span data-ttu-id="2280f-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2280f-127">win:UInt32</span></span>|<span data-ttu-id="2280f-128">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2280f-128">The HResult error code.</span></span>|  
|<span data-ttu-id="2280f-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="2280f-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="2280f-130">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2280f-130">win:UnicodeString</span></span>|<span data-ttu-id="2280f-131">完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="2280f-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="2280f-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2280f-132">ClrInstanceID</span></span>|<span data-ttu-id="2280f-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2280f-133">win:UInt16</span></span>|<span data-ttu-id="2280f-134">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="2280f-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="2280f-135">AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="2280f-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="2280f-136">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="2280f-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2280f-137">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2280f-137">Keyword for raising the event</span></span>|<span data-ttu-id="2280f-138">Level</span><span class="sxs-lookup"><span data-stu-id="2280f-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2280f-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="2280f-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="2280f-140">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="2280f-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="2280f-141">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="2280f-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2280f-142">Event</span><span class="sxs-lookup"><span data-stu-id="2280f-142">Event</span></span>|<span data-ttu-id="2280f-143">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2280f-143">Event ID</span></span>|<span data-ttu-id="2280f-144">引發的時機</span><span class="sxs-lookup"><span data-stu-id="2280f-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="2280f-145">183</span><span class="sxs-lookup"><span data-stu-id="2280f-145">183</span></span>|<span data-ttu-id="2280f-146">Authenticode 驗證的開頭。</span><span class="sxs-lookup"><span data-stu-id="2280f-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="2280f-147">184</span><span class="sxs-lookup"><span data-stu-id="2280f-147">184</span></span>|<span data-ttu-id="2280f-148">Authenticode 驗證的結尾。</span><span class="sxs-lookup"><span data-stu-id="2280f-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="2280f-149">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="2280f-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2280f-150">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="2280f-150">Field name</span></span>|<span data-ttu-id="2280f-151">資料類型</span><span class="sxs-lookup"><span data-stu-id="2280f-151">Data type</span></span>|<span data-ttu-id="2280f-152">描述</span><span class="sxs-lookup"><span data-stu-id="2280f-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2280f-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="2280f-153">VerificationFlags</span></span>|<span data-ttu-id="2280f-154">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2280f-154">win:UInt32</span></span>|<span data-ttu-id="2280f-155">驗證旗標。</span><span class="sxs-lookup"><span data-stu-id="2280f-155">The verification flags.</span></span>|  
|<span data-ttu-id="2280f-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="2280f-156">ErrorCode</span></span>|<span data-ttu-id="2280f-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2280f-157">win:UInt32</span></span>|<span data-ttu-id="2280f-158">HResult 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2280f-158">The HResult error code.</span></span>|  
|<span data-ttu-id="2280f-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="2280f-159">ModulePath</span></span>|<span data-ttu-id="2280f-160">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2280f-160">win:UnicodeString</span></span>|<span data-ttu-id="2280f-161">模組路徑。</span><span class="sxs-lookup"><span data-stu-id="2280f-161">The module path.</span></span>|  
|<span data-ttu-id="2280f-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2280f-162">ClrInstanceID</span></span>|<span data-ttu-id="2280f-163">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2280f-163">win:UInt16</span></span>|<span data-ttu-id="2280f-164">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="2280f-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2280f-165">請參閱</span><span class="sxs-lookup"><span data-stu-id="2280f-165">See also</span></span>

- [<span data-ttu-id="2280f-166">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="2280f-166">CLR ETW Events</span></span>](clr-etw-events.md)
