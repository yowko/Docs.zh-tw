---
title: ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136577"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="bffea-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="bffea-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="bffea-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="bffea-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="bffea-104">每當動態方法的 JIT 編譯完成時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="bffea-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bffea-105">語法</span><span class="sxs-lookup"><span data-stu-id="bffea-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bffea-106">參數</span><span class="sxs-lookup"><span data-stu-id="bffea-106">Parameters</span></span>  
<span data-ttu-id="bffea-107">[輸入] `functionId`</span><span class="sxs-lookup"><span data-stu-id="bffea-107">[in] `functionId`</span></span>  
<span data-ttu-id="bffea-108">啟動 JIT 編譯之記憶體中函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bffea-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="bffea-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="bffea-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="bffea-110">值，指出 JIT 編譯是否成功。</span><span class="sxs-lookup"><span data-stu-id="bffea-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="bffea-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="bffea-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="bffea-112">`true`，表示封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回;`false`，表示封鎖作業不會影響執行時間的作業。</span><span class="sxs-lookup"><span data-stu-id="bffea-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="bffea-113">備註</span><span class="sxs-lookup"><span data-stu-id="bffea-113">Remarks</span></span>  

<span data-ttu-id="bffea-114">每當動態方法的 JIT 編譯完成時，就會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="bffea-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="bffea-115">這包括各種 IL stub 和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="bffea-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="bffea-116">其目標是要為 profiler 寫入器提供足夠的資訊，以向使用者識別已編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="bffea-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="bffea-117">`functionId` 值無法用來解析其元資料標記，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bffea-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="bffea-118">需求</span><span class="sxs-lookup"><span data-stu-id="bffea-118">Requirements</span></span>  
 <span data-ttu-id="bffea-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bffea-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bffea-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bffea-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bffea-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bffea-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bffea-122">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bffea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffea-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="bffea-123">See also</span></span>

- [<span data-ttu-id="bffea-124">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="bffea-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="bffea-125">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="bffea-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
