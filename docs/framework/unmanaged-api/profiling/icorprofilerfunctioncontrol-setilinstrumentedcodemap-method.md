---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: d22d789724a62cebb0136b9b01be22d6825384ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714532"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="07326-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap 方法</span><span class="sxs-lookup"><span data-stu-id="07326-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="07326-103">使用指定的通用中間語言 (CIL) 對應項目，為所指定的函式設定程式碼對應。</span><span class="sxs-lookup"><span data-stu-id="07326-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07326-104">語法</span><span class="sxs-lookup"><span data-stu-id="07326-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07326-105">參數</span><span class="sxs-lookup"><span data-stu-id="07326-105">Parameters</span></span>  

 `cILMapEntries`  
 <span data-ttu-id="07326-106">[in] 對應中的項目數。</span><span class="sxs-lookup"><span data-stu-id="07326-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="07326-107">[in] COR_IL_MAP 項目的呼叫端配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="07326-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="07326-108">這些專案的解讀與 [ICorProfilerInfo：： SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) 方法的解讀相同。</span><span class="sxs-lookup"><span data-stu-id="07326-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07326-109">備註</span><span class="sxs-lookup"><span data-stu-id="07326-109">Remarks</span></span>  

 <span data-ttu-id="07326-110">藉由呼叫這個方法來設定對應，可讓偵錯工具藉由呼叫 [ICorDebugILCode2：： GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md)來取得對應。</span><span class="sxs-lookup"><span data-stu-id="07326-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="07326-111">這也可以讓偵錯工具在計算堆疊追蹤及變數存留期的 IL 位移時於內部使用對應。</span><span class="sxs-lookup"><span data-stu-id="07326-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07326-112">需求</span><span class="sxs-lookup"><span data-stu-id="07326-112">Requirements</span></span>  

 <span data-ttu-id="07326-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07326-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07326-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07326-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07326-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07326-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07326-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07326-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07326-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07326-117">See also</span></span>

- [<span data-ttu-id="07326-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="07326-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
