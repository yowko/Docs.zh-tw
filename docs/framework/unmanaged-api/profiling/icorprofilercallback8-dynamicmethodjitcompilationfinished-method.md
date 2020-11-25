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
ms.openlocfilehash: 6354667e754da42692cc0de2dc5330c56f951aa1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725439"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="6dfd1-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="6dfd1-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="6dfd1-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="6dfd1-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="6dfd1-104">每當動態方法的 JIT 編譯完成時，通知 profiler。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfd1-105">語法</span><span class="sxs-lookup"><span data-stu-id="6dfd1-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dfd1-106">參數</span><span class="sxs-lookup"><span data-stu-id="6dfd1-106">Parameters</span></span>  

<span data-ttu-id="6dfd1-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="6dfd1-107">[in] `functionId`</span></span>  
<span data-ttu-id="6dfd1-108">已啟動 JIT 編譯之記憶體內建函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="6dfd1-109">[in] `hrStatus` 指出 JIT 編譯是否成功的值。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="6dfd1-110">[in] `fIsSafeToBlock` 
 `true`若要指出封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回;`false`表示封鎖不會影響執行時間的操作。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="6dfd1-111">備註</span><span class="sxs-lookup"><span data-stu-id="6dfd1-111">Remarks</span></span>  

<span data-ttu-id="6dfd1-112">每當動態方法的 JIT 編譯完成時，就會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="6dfd1-113">這包括各種 IL 存根和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="6dfd1-114">其目標是要為 profiler 寫入器提供足夠的資訊，以識別已編譯的方法給使用者。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="6dfd1-115">`functionId` 因為動態方法沒有中繼資料，所以無法使用值解析其元資料標記。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="6dfd1-116">需求</span><span class="sxs-lookup"><span data-stu-id="6dfd1-116">Requirements</span></span>  

 <span data-ttu-id="6dfd1-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfd1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfd1-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dfd1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dfd1-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dfd1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dfd1-120">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfd1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfd1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dfd1-121">See also</span></span>

- [<span data-ttu-id="6dfd1-122">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="6dfd1-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="6dfd1-123">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="6dfd1-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
