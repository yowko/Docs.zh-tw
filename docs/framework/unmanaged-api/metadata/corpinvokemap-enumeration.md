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
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441554"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="cd2c4-102">CorPinvokeMap 列舉</span><span class="sxs-lookup"><span data-stu-id="cd2c4-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="cd2c4-103">指定 PInvoke 呼叫的選項。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd2c4-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cd2c4-105">Members</span><span class="sxs-lookup"><span data-stu-id="cd2c4-105">Members</span></span>  
  
|<span data-ttu-id="cd2c4-106">成員</span><span class="sxs-lookup"><span data-stu-id="cd2c4-106">Member</span></span>|<span data-ttu-id="cd2c4-107">描述</span><span class="sxs-lookup"><span data-stu-id="cd2c4-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="cd2c4-108">使用指定的每個成員名稱。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="cd2c4-109">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="cd2c4-110">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="cd2c4-111">將字串封送處理為多位元組字元字串。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="cd2c4-112">將字串封送處理為 Unicode 2 位元組字元。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="cd2c4-113">會自動封送處理目標作業系統的字串。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="cd2c4-114">Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 系列上的預設值為 Unicode;Windows 98 和 Windows Me 上的預設值是 ANSI。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="cd2c4-115">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="cd2c4-116">執行 Unicode 字元的自動調整對應，其在 ANSI 字元集中缺少完全相符的項。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="cd2c4-117">請勿執行 Unicode 字元的自動調整對應。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="cd2c4-118">在此情況下，所有無法映射的字元都會由 '？ ' 取代。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="cd2c4-119">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="cd2c4-120">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="cd2c4-121">當 interop 封送處理器遇到無法映射的字元時，擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="cd2c4-122">當 interop 封送處理器遇到無法映射的字元時，不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="cd2c4-123">保留</span><span class="sxs-lookup"><span data-stu-id="cd2c4-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="cd2c4-124">允許被呼叫者先呼叫 Win32 `SetLastError` 函式，然後再從屬性化方法傳回。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="cd2c4-125">保留</span><span class="sxs-lookup"><span data-stu-id="cd2c4-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="cd2c4-126">使用預設的平臺呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-126">Use the default platform calling convention.</span></span> <span data-ttu-id="cd2c4-127">例如，在 Windows 上，預設值是 `StdCall`，而 Windows CE .NET 則 `Cdecl`。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="cd2c4-128">使用 `Cdecl` 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="cd2c4-129">在此情況下，呼叫端會清除堆疊。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="cd2c4-130">這可讓您使用 `varargs` （也就是接受可變數目參數的函式）來呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="cd2c4-131">使用 `StdCall` 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="cd2c4-132">在此情況下，被呼叫端會清除堆疊。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="cd2c4-133">這是使用平台叫用來呼叫非受控函式的預設慣例。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="cd2c4-134">使用 `ThisCall` 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="cd2c4-135">在此情況下，第一個參數是 `this` 指標，並儲存在 register ECX 中。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="cd2c4-136">堆疊上會推送其他參數。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="cd2c4-137">`ThisCall` 呼叫慣例是用來在從非受控 DLL 匯出的類別上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="cd2c4-138">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="cd2c4-139">保留。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd2c4-140">需求</span><span class="sxs-lookup"><span data-stu-id="cd2c4-140">Requirements</span></span>  
 <span data-ttu-id="cd2c4-141">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2c4-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2c4-142">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="cd2c4-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cd2c4-143">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2c4-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2c4-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd2c4-144">See also</span></span>

- [<span data-ttu-id="cd2c4-145">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="cd2c4-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
