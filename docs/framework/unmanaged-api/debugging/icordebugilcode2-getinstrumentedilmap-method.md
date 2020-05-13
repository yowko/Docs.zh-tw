---
title: ICorDebugILCode2::GetInstrumentedILMap 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: c6fdb7040620bb7a5b6aea6e0dc41e08d6f346d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210354"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="d0fcf-102">ICorDebugILCode2::GetInstrumentedILMap 方法</span><span class="sxs-lookup"><span data-stu-id="d0fcf-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="d0fcf-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="d0fcf-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d0fcf-104">將對應從分析工具檢測中繼語言 (IL) 位移傳回至此執行個體的原始方法 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0fcf-105">語法</span><span class="sxs-lookup"><span data-stu-id="d0fcf-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0fcf-106">參數</span><span class="sxs-lookup"><span data-stu-id="d0fcf-106">Parameters</span></span>  
 <span data-ttu-id="d0fcf-107">cMap</span><span class="sxs-lookup"><span data-stu-id="d0fcf-107">cMap</span></span>  
 <span data-ttu-id="d0fcf-108">[in] `map` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="d0fcf-109">如需詳細資訊，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="d0fcf-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="d0fcf-110">pcMap</span></span>  
 <span data-ttu-id="d0fcf-111">[out] 寫入至對應陣列的 COR_IL_MAP 值數目。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="d0fcf-112">map</span><span class="sxs-lookup"><span data-stu-id="d0fcf-112">map</span></span>  
 <span data-ttu-id="d0fcf-113">[out] COR_IL_MAP 值陣列，這些值提供從分析工具檢測 IL 對應至原始方法 IL 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0fcf-114">備註</span><span class="sxs-lookup"><span data-stu-id="d0fcf-114">Remarks</span></span>  
 <span data-ttu-id="d0fcf-115">如果分析工具藉由呼叫[ICorProfilerInfo：： SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)方法來設定對應，偵錯工具就可以呼叫這個方法來抓取對應，並在計算堆疊追蹤和變數存留期的 IL 位移時，在內部使用對應。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="d0fcf-116">如果 `cMap` 為0，且 `pcMap` 為非**null**， `pcMap` 則會設定為可用 COR_IL_MAP 值的數目。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="d0fcf-117">如果 `cMap` 不是零，則代表 `map` 陣列的儲存體容量。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="d0fcf-118">當此方法傳回時， `map` 會包含最多個 `cMap` 專案，而且 `pcMap` 會設定為實際寫入陣列的 COR_IL_MAP 值數目 `map` 。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="d0fcf-119">如果 IL 未經檢測，或是分析工具未提供對應，此方法會傳回 `S_OK`，並將 `pcMap` 設為 0。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0fcf-120">需求</span><span class="sxs-lookup"><span data-stu-id="d0fcf-120">Requirements</span></span>  
 <span data-ttu-id="d0fcf-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0fcf-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0fcf-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0fcf-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0fcf-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0fcf-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0fcf-124">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0fcf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fcf-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0fcf-125">See also</span></span>

- [<span data-ttu-id="d0fcf-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="d0fcf-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="d0fcf-127">ICorDebugILCode2 介面</span><span class="sxs-lookup"><span data-stu-id="d0fcf-127">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="d0fcf-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d0fcf-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
