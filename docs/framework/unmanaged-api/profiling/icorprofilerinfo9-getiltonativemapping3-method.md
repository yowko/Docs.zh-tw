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
ms.openlocfilehash: 5c49d75432980d2f3af77ee040bc6eb20886b027
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861667"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="eee29-102">ICorProfilerInfo9：： GetILToNativeMapping3 方法</span><span class="sxs-lookup"><span data-stu-id="eee29-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="eee29-103">假設機器碼的起始位址，會傳回這個程式碼編譯版本的原生到 IL 對應資訊。</span><span class="sxs-lookup"><span data-stu-id="eee29-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="eee29-104">語法</span><span class="sxs-lookup"><span data-stu-id="eee29-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="eee29-105">參數</span><span class="sxs-lookup"><span data-stu-id="eee29-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="eee29-106">中的 \[]：原生函式開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="eee29-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="eee29-107">\[in] `map` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="eee29-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="eee29-108">\[out] 可用 COR_DEBUG_IL_TO_NATIVE_MAP 結構的總數。</span><span class="sxs-lookup"><span data-stu-id="eee29-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="eee29-109">\[out] [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md)結構的陣列，其中每一個都會指定位移。</span><span class="sxs-lookup"><span data-stu-id="eee29-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="eee29-110">`GetILToNativeMapping3` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。</span><span class="sxs-lookup"><span data-stu-id="eee29-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="eee29-111">備註</span><span class="sxs-lookup"><span data-stu-id="eee29-111">Remarks</span></span>

<span data-ttu-id="eee29-112">啟用階層式編譯時，方法可能會有一個以上的機器碼主體。</span><span class="sxs-lookup"><span data-stu-id="eee29-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="eee29-113">[ICorProfilerInfo9：： GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)會傳回所有機器碼主體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="eee29-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="eee29-114">需求</span><span class="sxs-lookup"><span data-stu-id="eee29-114">Requirements</span></span>

<span data-ttu-id="eee29-115">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="eee29-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="eee29-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eee29-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="eee29-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eee29-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="eee29-118">**.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee29-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="eee29-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="eee29-119">See also</span></span>

- [<span data-ttu-id="eee29-120">ICorProfilerInfo9 介面</span><span class="sxs-lookup"><span data-stu-id="eee29-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
