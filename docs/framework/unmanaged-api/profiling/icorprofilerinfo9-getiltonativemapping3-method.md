---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9e8e4c7e6c367970100c98dc3dc8237b25f99221
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665607"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="d809f-102">ICorProfilerInfo9:: GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="d809f-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="d809f-103">假設機器碼的起始位址, 會傳回這個程式碼編譯版本的原生到 IL 對應資訊。</span><span class="sxs-lookup"><span data-stu-id="d809f-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="d809f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d809f-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a><span data-ttu-id="d809f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d809f-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="d809f-106">在原生函式開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="d809f-106">[in] A pointer to the start of a native function.</span></span>

`cMap` \
<span data-ttu-id="d809f-107">[in] `map` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="d809f-107">[in] The maximum size of the `map` array.</span></span>

`pcMap` \
<span data-ttu-id="d809f-108">脫銷可用的 COR_DEBUG_IL_TO_NATIVE_MAP 結構總數。</span><span class="sxs-lookup"><span data-stu-id="d809f-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

`map` \
<span data-ttu-id="d809f-109">脫銷[COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md)結構的陣列, 其中每一個都會指定位移。</span><span class="sxs-lookup"><span data-stu-id="d809f-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="d809f-110">`GetILToNativeMapping3` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。</span><span class="sxs-lookup"><span data-stu-id="d809f-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="d809f-111">備註</span><span class="sxs-lookup"><span data-stu-id="d809f-111">Remarks</span></span>

<span data-ttu-id="d809f-112">啟用階層式編譯時, 方法可能會有一個以上的機器碼主體。</span><span class="sxs-lookup"><span data-stu-id="d809f-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="d809f-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)會傳回所有機器碼主體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="d809f-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="d809f-114">需求</span><span class="sxs-lookup"><span data-stu-id="d809f-114">Requirements</span></span>

<span data-ttu-id="d809f-115">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="d809f-115">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="d809f-116">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="d809f-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d809f-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d809f-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d809f-118">**.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d809f-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d809f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d809f-119">See also</span></span>

- [<span data-ttu-id="d809f-120">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="d809f-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
