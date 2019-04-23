---
title: CorPinvokeMap 列舉
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079626"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="b977b-102">CorPinvokeMap 列舉</span><span class="sxs-lookup"><span data-stu-id="b977b-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="b977b-103">指定的 PInvoke 呼叫的選項。</span><span class="sxs-lookup"><span data-stu-id="b977b-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b977b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b977b-104">Syntax</span></span>  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="b977b-105">成員</span><span class="sxs-lookup"><span data-stu-id="b977b-105">Members</span></span>  
  
|<span data-ttu-id="b977b-106">成員</span><span class="sxs-lookup"><span data-stu-id="b977b-106">Member</span></span>|<span data-ttu-id="b977b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b977b-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="b977b-108">使用所指定的每個成員名稱。</span><span class="sxs-lookup"><span data-stu-id="b977b-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="b977b-109">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="b977b-110">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="b977b-111">封送處理成多位元組字元字串的字串。</span><span class="sxs-lookup"><span data-stu-id="b977b-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="b977b-112">封送處理為 Unicode 2 個位元組字元的字串。</span><span class="sxs-lookup"><span data-stu-id="b977b-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="b977b-113">自動字串封送處理適當的目標作業系統。</span><span class="sxs-lookup"><span data-stu-id="b977b-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="b977b-114">預設值是 Windows NT、 Windows 2000，Windows XP 和 Windows Server 2003 系列中 Unicode預設值是 Windows 98 和 Windows me 上的為 ANSI</span><span class="sxs-lookup"><span data-stu-id="b977b-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="b977b-115">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="b977b-116">執行沒有完全符合 ANSI 字元集中的 Unicode 字元的自動調整的對應。</span><span class="sxs-lookup"><span data-stu-id="b977b-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="b977b-117">不會執行自動調整的對應的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="b977b-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="b977b-118">在此情況下，所有無法對應的字元會取代 '？ '。</span><span class="sxs-lookup"><span data-stu-id="b977b-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="b977b-119">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="b977b-120">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="b977b-121">Interop 封送處理器遇到無法對應的字元時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b977b-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="b977b-122">Interop 封送處理器遇到無法對應的字元時，請務必擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b977b-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="b977b-123">保留</span><span class="sxs-lookup"><span data-stu-id="b977b-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="b977b-124">可讓被呼叫端呼叫 Win32`SetLastError`自屬性方法傳回之前的函式。</span><span class="sxs-lookup"><span data-stu-id="b977b-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="b977b-125">保留</span><span class="sxs-lookup"><span data-stu-id="b977b-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="b977b-126">使用預設平台呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="b977b-126">Use the default platform calling convention.</span></span> <span data-ttu-id="b977b-127">比方說，在 Windows 上的預設值是`StdCall`以及它是 Windows CE.NET `Cdecl`。</span><span class="sxs-lookup"><span data-stu-id="b977b-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="b977b-128">使用`Cdecl`呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="b977b-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="b977b-129">在此情況下，呼叫端會清除堆疊。</span><span class="sxs-lookup"><span data-stu-id="b977b-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="b977b-130">這可讓呼叫的函式與`varargs`（也就是函式接受變動數目的參數）。</span><span class="sxs-lookup"><span data-stu-id="b977b-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="b977b-131">使用`StdCall`呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="b977b-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="b977b-132">在此情況下，被呼叫端會清除堆疊。</span><span class="sxs-lookup"><span data-stu-id="b977b-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="b977b-133">這是呼叫 unmanaged 函式，與平台叫用的預設慣例。</span><span class="sxs-lookup"><span data-stu-id="b977b-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="b977b-134">使用`ThisCall`呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="b977b-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="b977b-135">在此案例中，第一個參數是`this`指標儲存在 register ECX 和。</span><span class="sxs-lookup"><span data-stu-id="b977b-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="b977b-136">其他參數會推送到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="b977b-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="b977b-137">`ThisCall`呼叫慣例用來呼叫從 unmanaged DLL 匯出的類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="b977b-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="b977b-138">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="b977b-139">保留的。</span><span class="sxs-lookup"><span data-stu-id="b977b-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b977b-140">需求</span><span class="sxs-lookup"><span data-stu-id="b977b-140">Requirements</span></span>  
 <span data-ttu-id="b977b-141">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b977b-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b977b-142">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b977b-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b977b-143">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b977b-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b977b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b977b-144">See also</span></span>

- [<span data-ttu-id="b977b-145">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="b977b-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
