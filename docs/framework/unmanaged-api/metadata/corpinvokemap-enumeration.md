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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176145"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="9abca-102">CorPinvokeMap 列舉</span><span class="sxs-lookup"><span data-stu-id="9abca-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="9abca-103">指定 PInvoke 調用的選項。</span><span class="sxs-lookup"><span data-stu-id="9abca-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abca-104">語法</span><span class="sxs-lookup"><span data-stu-id="9abca-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9abca-105">成員</span><span class="sxs-lookup"><span data-stu-id="9abca-105">Members</span></span>  
  
|<span data-ttu-id="9abca-106">member</span><span class="sxs-lookup"><span data-stu-id="9abca-106">Member</span></span>|<span data-ttu-id="9abca-107">描述</span><span class="sxs-lookup"><span data-stu-id="9abca-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="9abca-108">使用指定的每個成員名稱。</span><span class="sxs-lookup"><span data-stu-id="9abca-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="9abca-109">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="9abca-110">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="9abca-111">將字串當做多位元組字元字串來封送處理。</span><span class="sxs-lookup"><span data-stu-id="9abca-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="9abca-112">封送處理字串為 Unicode 2 個位元組字元。</span><span class="sxs-lookup"><span data-stu-id="9abca-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="9abca-113">自動為目標作業系統妥善地封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="9abca-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="9abca-114">預設值為 Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 系列上的 Unicode;預設值為 Windows 98 上的 ANSI 和 Windows Me。</span><span class="sxs-lookup"><span data-stu-id="9abca-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="9abca-115">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="9abca-116">對 ANSI 字元集中缺少完全符合的 Unicode 字元執行最佳映射。</span><span class="sxs-lookup"><span data-stu-id="9abca-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="9abca-117">不要執行最適合的 Unicode 字元映射。</span><span class="sxs-lookup"><span data-stu-id="9abca-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="9abca-118">在這種情況下，所有不可映射的字元將替換為"？"。</span><span class="sxs-lookup"><span data-stu-id="9abca-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="9abca-119">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="9abca-120">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="9abca-121">當互通封送器遇到不可映射的字元時引發異常。</span><span class="sxs-lookup"><span data-stu-id="9abca-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="9abca-122">當互通封送器遇到不可映射的字元時，不要引發異常。</span><span class="sxs-lookup"><span data-stu-id="9abca-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="9abca-123">Reserved</span><span class="sxs-lookup"><span data-stu-id="9abca-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="9abca-124">允許被調用人調用 Win32`SetLastError`函數，然後再從屬性化方法返回。</span><span class="sxs-lookup"><span data-stu-id="9abca-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="9abca-125">Reserved</span><span class="sxs-lookup"><span data-stu-id="9abca-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="9abca-126">使用預設平台叫用約定。</span><span class="sxs-lookup"><span data-stu-id="9abca-126">Use the default platform calling convention.</span></span> <span data-ttu-id="9abca-127">例如，在 Windows 上，`StdCall`預設值為 ，在 Windows `Cdecl`CE .NET 上，預設值為 。</span><span class="sxs-lookup"><span data-stu-id="9abca-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="9abca-128">使用`Cdecl`調用約定。</span><span class="sxs-lookup"><span data-stu-id="9abca-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="9abca-129">在這種情況下，調用方清理堆疊。</span><span class="sxs-lookup"><span data-stu-id="9abca-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="9abca-130">這允許調用函數（`varargs`即接受可變數量的參數的函數）。</span><span class="sxs-lookup"><span data-stu-id="9abca-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="9abca-131">使用`StdCall`調用約定。</span><span class="sxs-lookup"><span data-stu-id="9abca-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="9abca-132">在這種情況下，被叫人清理堆疊。</span><span class="sxs-lookup"><span data-stu-id="9abca-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="9abca-133">這是針對用平台叫用呼叫 Unmanaged 函式的預設慣例。</span><span class="sxs-lookup"><span data-stu-id="9abca-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="9abca-134">使用`ThisCall`調用約定。</span><span class="sxs-lookup"><span data-stu-id="9abca-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="9abca-135">在這種情況下，第一個參數是指標，`this`並存儲在寄存器 ECX 中。</span><span class="sxs-lookup"><span data-stu-id="9abca-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="9abca-136">其他參數會被推入至堆疊。</span><span class="sxs-lookup"><span data-stu-id="9abca-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="9abca-137">調用`ThisCall`約定用於調用從非託管 DLL 匯出的類上的方法。</span><span class="sxs-lookup"><span data-stu-id="9abca-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="9abca-138">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="9abca-139">已保留。</span><span class="sxs-lookup"><span data-stu-id="9abca-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9abca-140">需求</span><span class="sxs-lookup"><span data-stu-id="9abca-140">Requirements</span></span>  
 <span data-ttu-id="9abca-141">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9abca-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9abca-142">**標題：** 科爾赫德</span><span class="sxs-lookup"><span data-stu-id="9abca-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9abca-143">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9abca-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abca-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9abca-144">See also</span></span>

- [<span data-ttu-id="9abca-145">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="9abca-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
