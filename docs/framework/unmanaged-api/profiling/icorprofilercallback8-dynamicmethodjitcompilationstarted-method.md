---
title: ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136469"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="fc125-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="fc125-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="fc125-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="fc125-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="fc125-104">每當動態方法的 JIT 編譯開始時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="fc125-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc125-105">語法</span><span class="sxs-lookup"><span data-stu-id="fc125-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc125-106">參數</span><span class="sxs-lookup"><span data-stu-id="fc125-106">Parameters</span></span>  
<span data-ttu-id="fc125-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="fc125-107">[in] `functionId`</span></span>  
<span data-ttu-id="fc125-108">啟動 JIT 編譯之記憶體中函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc125-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="fc125-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="fc125-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="fc125-110">`true`，表示封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回;`false`，表示封鎖作業不會影響執行時間的作業。</span><span class="sxs-lookup"><span data-stu-id="fc125-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="fc125-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="fc125-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="fc125-112">方法的 IL 標頭的第一個位元組指標。</span><span class="sxs-lookup"><span data-stu-id="fc125-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="fc125-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="fc125-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="fc125-114">IL 標頭中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="fc125-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="fc125-115">備註</span><span class="sxs-lookup"><span data-stu-id="fc125-115">Remarks</span></span>  

<span data-ttu-id="fc125-116">每當動態方法是 JIT 編譯時，就會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="fc125-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="fc125-117">這包括各種 IL stub 和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="fc125-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="fc125-118">其目標是要為 profiler 寫入器提供足夠的資訊，以向使用者識別已編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="fc125-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="fc125-119">`functionId` 值無法用來解析其元資料標記，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fc125-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="fc125-120">`pILHeader` 指標只有在回呼期間有效。</span><span class="sxs-lookup"><span data-stu-id="fc125-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc125-121">需求</span><span class="sxs-lookup"><span data-stu-id="fc125-121">Requirements</span></span>  
 <span data-ttu-id="fc125-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc125-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc125-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc125-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc125-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc125-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc125-125">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fc125-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc125-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc125-126">See also</span></span>

- [<span data-ttu-id="fc125-127">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fc125-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="fc125-128">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="fc125-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
