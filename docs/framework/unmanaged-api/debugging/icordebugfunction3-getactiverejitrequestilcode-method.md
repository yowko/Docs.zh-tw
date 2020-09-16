---
title: ICorDebugFunction3::GetActiveReJitRequestILCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 8c502c082c2cf90d87c195df531de686e2a6d914
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544254"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="8b38b-102">ICorDebugFunction3::GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="8b38b-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="8b38b-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="8b38b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8b38b-104">從使用中的 ReJIT 要求取得包含 IL 的 [ICorDebugILCode](icordebugilcode-interface.md) 介面指標。</span><span class="sxs-lookup"><span data-stu-id="8b38b-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b38b-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b38b-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b38b-106">參數</span><span class="sxs-lookup"><span data-stu-id="8b38b-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="8b38b-107">作用中 ReJIT 要求之 IL 的指標。</span><span class="sxs-lookup"><span data-stu-id="8b38b-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b38b-108">備註</span><span class="sxs-lookup"><span data-stu-id="8b38b-108">Remarks</span></span>  
 <span data-ttu-id="8b38b-109">如果此 `ICorDebugFunction3` 物件所代表的方法具有作用中 ReJIT 要求，則 `ppReJitedILCode` 會傳回其 IL 的指標。</span><span class="sxs-lookup"><span data-stu-id="8b38b-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="8b38b-110">如果沒有作用中的要求，這是常見的情況，則 `ppReJitedILCode` 為 **null**。</span><span class="sxs-lookup"><span data-stu-id="8b38b-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="8b38b-111">當執行從 [ICorProfilerCallback4：： GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) 方法呼叫傳回之後，ReJIT 要求就會變成作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="8b38b-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="8b38b-112">該要求可能未經 JIT 編譯，而執行緒可能仍在原始版本程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="8b38b-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="8b38b-113">在分析工具的 [ICorProfilerInfo4：： RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) 方法呼叫期間，ReJIT 要求變成非使用中。</span><span class="sxs-lookup"><span data-stu-id="8b38b-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="8b38b-114">即使在 IL 還原之後，執行緒仍可在 JIT 重新編譯的 (ReJIT) 程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="8b38b-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b38b-115">需求</span><span class="sxs-lookup"><span data-stu-id="8b38b-115">Requirements</span></span>  
 <span data-ttu-id="8b38b-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b38b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b38b-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b38b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b38b-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b38b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b38b-119">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b38b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b38b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b38b-120">See also</span></span>

- [<span data-ttu-id="8b38b-121">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="8b38b-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="8b38b-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8b38b-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8b38b-123">ReJIT：操作指南</span><span class="sxs-lookup"><span data-stu-id="8b38b-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
