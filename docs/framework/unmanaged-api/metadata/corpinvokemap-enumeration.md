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
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007542"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="03316-102">CorPinvokeMap 列舉</span><span class="sxs-lookup"><span data-stu-id="03316-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="03316-103">指定 PInvoke 呼叫的選項。</span><span class="sxs-lookup"><span data-stu-id="03316-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03316-104">語法</span><span class="sxs-lookup"><span data-stu-id="03316-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="03316-105">成員</span><span class="sxs-lookup"><span data-stu-id="03316-105">Members</span></span>  
  
|<span data-ttu-id="03316-106">成員</span><span class="sxs-lookup"><span data-stu-id="03316-106">Member</span></span>|<span data-ttu-id="03316-107">描述</span><span class="sxs-lookup"><span data-stu-id="03316-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="03316-108">使用指定的每個成員名稱。</span><span class="sxs-lookup"><span data-stu-id="03316-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="03316-109">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="03316-110">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="03316-111">將字串當做多位元組字元字串來封送處理。</span><span class="sxs-lookup"><span data-stu-id="03316-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="03316-112">封送處理字串為 Unicode 2 個位元組字元。</span><span class="sxs-lookup"><span data-stu-id="03316-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="03316-113">自動為目標作業系統妥善地封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="03316-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="03316-114">Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 系列上的預設值為 Unicode;Windows 98 和 Windows Me 上的預設值是 ANSI。</span><span class="sxs-lookup"><span data-stu-id="03316-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="03316-115">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="03316-116">執行 Unicode 字元的自動調整對應，其在 ANSI 字元集中缺少完全相符的項。</span><span class="sxs-lookup"><span data-stu-id="03316-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="03316-117">請勿執行 Unicode 字元的自動調整對應。</span><span class="sxs-lookup"><span data-stu-id="03316-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="03316-118">在此情況下，所有無法映射的字元都會由 '？ ' 取代。</span><span class="sxs-lookup"><span data-stu-id="03316-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="03316-119">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="03316-120">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="03316-121">當 interop 封送處理器遇到無法映射的字元時，擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="03316-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="03316-122">當 interop 封送處理器遇到無法映射的字元時，不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="03316-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="03316-123">Reserved</span><span class="sxs-lookup"><span data-stu-id="03316-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="03316-124">允許被呼叫者在 `SetLastError` 從屬性化方法傳回之前呼叫 Win32 函式。</span><span class="sxs-lookup"><span data-stu-id="03316-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="03316-125">Reserved</span><span class="sxs-lookup"><span data-stu-id="03316-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="03316-126">使用預設的平臺呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="03316-126">Use the default platform calling convention.</span></span> <span data-ttu-id="03316-127">例如，在 Windows 上，預設值是 `StdCall` ，而在 Windows CE .net 則是 `Cdecl` 。</span><span class="sxs-lookup"><span data-stu-id="03316-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="03316-128">使用 `Cdecl` 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="03316-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="03316-129">在此情況下，呼叫端會清除堆疊。</span><span class="sxs-lookup"><span data-stu-id="03316-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="03316-130">這可讓使用呼叫函式 `varargs` （也就是接受可變數目參數的函式）。</span><span class="sxs-lookup"><span data-stu-id="03316-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="03316-131">使用 `StdCall` 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="03316-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="03316-132">在此情況下，被呼叫端會清除堆疊。</span><span class="sxs-lookup"><span data-stu-id="03316-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="03316-133">這是針對用平台叫用呼叫 Unmanaged 函式的預設慣例。</span><span class="sxs-lookup"><span data-stu-id="03316-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="03316-134">使用 `ThisCall` 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="03316-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="03316-135">在此情況下，第一個參數是 `this` 指標，並儲存在 REGISTER ECX 中。</span><span class="sxs-lookup"><span data-stu-id="03316-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="03316-136">其他參數會被推入至堆疊。</span><span class="sxs-lookup"><span data-stu-id="03316-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="03316-137">`ThisCall`呼叫慣例是用來在從非受控 DLL 匯出的類別上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="03316-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="03316-138">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="03316-139">已保留。</span><span class="sxs-lookup"><span data-stu-id="03316-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03316-140">需求</span><span class="sxs-lookup"><span data-stu-id="03316-140">Requirements</span></span>  
 <span data-ttu-id="03316-141">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03316-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03316-142">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="03316-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="03316-143">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03316-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03316-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03316-144">See also</span></span>

- [<span data-ttu-id="03316-145">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="03316-145">Metadata Enumerations</span></span>](metadata-enumerations.md)
