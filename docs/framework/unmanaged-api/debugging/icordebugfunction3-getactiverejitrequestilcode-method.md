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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4985a448321eceabf7975a8e5b638043f6c88723
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926846"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="0689d-102">ICorDebugFunction3::GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="0689d-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="0689d-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="0689d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0689d-104">取得[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)的介面指標，其中包含來自作用中 ReJIT 要求的 IL。</span><span class="sxs-lookup"><span data-stu-id="0689d-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0689d-105">語法</span><span class="sxs-lookup"><span data-stu-id="0689d-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0689d-106">參數</span><span class="sxs-lookup"><span data-stu-id="0689d-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="0689d-107">作用中 ReJIT 要求之 IL 的指標。</span><span class="sxs-lookup"><span data-stu-id="0689d-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0689d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0689d-108">Remarks</span></span>  
 <span data-ttu-id="0689d-109">如果此 `ICorDebugFunction3` 物件所代表的方法具有作用中 ReJIT 要求，則 `ppReJitedILCode` 會傳回其 IL 的指標。</span><span class="sxs-lookup"><span data-stu-id="0689d-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="0689d-110">如果沒有作用中的要求（這是常見的情況） `ppReJitedILCode` ，則為**null**。</span><span class="sxs-lookup"><span data-stu-id="0689d-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="0689d-111">在執行從[ICorProfilerCallback4：： GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)方法呼叫傳回之後，ReJIT 要求就會變成作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="0689d-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="0689d-112">該要求可能未經 JIT 編譯，而執行緒可能仍在原始版本程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="0689d-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="0689d-113">在分析工具的[ICorProfilerInfo4：： RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)方法呼叫期間，ReJIT 要求變成非作用中。</span><span class="sxs-lookup"><span data-stu-id="0689d-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="0689d-114">即使在 IL 還原之後，執行緒仍可在 JIT 重新編譯的 (ReJIT) 程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="0689d-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0689d-115">需求</span><span class="sxs-lookup"><span data-stu-id="0689d-115">Requirements</span></span>  
 <span data-ttu-id="0689d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0689d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0689d-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0689d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0689d-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0689d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0689d-119">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0689d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0689d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0689d-120">See also</span></span>

- [<span data-ttu-id="0689d-121">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="0689d-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="0689d-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0689d-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0689d-123">ReJIT使用說明指南</span><span class="sxs-lookup"><span data-stu-id="0689d-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
