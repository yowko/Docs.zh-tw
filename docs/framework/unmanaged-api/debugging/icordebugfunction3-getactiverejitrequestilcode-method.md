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
ms.openlocfilehash: 6268019f2e65c7c9209e00c0b6065e91103980c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115878"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="1e1d8-102">ICorDebugFunction3::GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="1e1d8-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="1e1d8-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="1e1d8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1e1d8-104">取得的介面指標[ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) ，其中包含作用中 ReJIT 要求之 IL。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e1d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="1e1d8-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e1d8-106">參數</span><span class="sxs-lookup"><span data-stu-id="1e1d8-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="1e1d8-107">作用中 ReJIT 要求之 IL 的指標。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e1d8-108">備註</span><span class="sxs-lookup"><span data-stu-id="1e1d8-108">Remarks</span></span>  
 <span data-ttu-id="1e1d8-109">如果此 `ICorDebugFunction3` 物件所代表的方法具有作用中 ReJIT 要求，則 `ppReJitedILCode` 會傳回其 IL 的指標。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="1e1d8-110">如果沒有任何作用中要求，也就是常見的情況，然後`ppReJitedILCode`已**null**。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="1e1d8-111">從傳回的執行之後，ReJIT 要求變成作用[ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="1e1d8-112">該要求可能未經 JIT 編譯，而執行緒可能仍在原始版本程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="1e1d8-113">分析工具的呼叫期間變成非作用中 ReJIT 要求[ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="1e1d8-114">即使在 IL 還原之後，執行緒仍可在 JIT 重新編譯的 (ReJIT) 程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e1d8-115">需求</span><span class="sxs-lookup"><span data-stu-id="1e1d8-115">Requirements</span></span>  
 <span data-ttu-id="1e1d8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e1d8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e1d8-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e1d8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e1d8-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e1d8-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1e1d8-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="1e1d8-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1e1d8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e1d8-120">See also</span></span>

- [<span data-ttu-id="1e1d8-121">ICorDebugFunction3 介面</span><span class="sxs-lookup"><span data-stu-id="1e1d8-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="1e1d8-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1e1d8-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1e1d8-123">ReJIT:操作說明指南</span><span class="sxs-lookup"><span data-stu-id="1e1d8-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
