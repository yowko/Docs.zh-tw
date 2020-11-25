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
ms.openlocfilehash: 46a25fc6e9119481f728275e0569429cc6c46dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725426"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="34d92-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="34d92-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="34d92-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="34d92-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="34d92-104">每當動態方法的 JIT 編譯開始時，通知 profiler。</span><span class="sxs-lookup"><span data-stu-id="34d92-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d92-105">語法</span><span class="sxs-lookup"><span data-stu-id="34d92-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34d92-106">參數</span><span class="sxs-lookup"><span data-stu-id="34d92-106">Parameters</span></span>  

<span data-ttu-id="34d92-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="34d92-107">[in] `functionId`</span></span>  
<span data-ttu-id="34d92-108">已啟動 JIT 編譯之記憶體內建函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="34d92-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="34d92-109">[in] `fIsSafeToBlock` 
 `true`若要指出封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回;`false`表示封鎖不會影響執行時間的操作。</span><span class="sxs-lookup"><span data-stu-id="34d92-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="34d92-110">[in] `pILHeader` 方法 IL 標頭第一個位元組的指標。</span><span class="sxs-lookup"><span data-stu-id="34d92-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="34d92-111">[in] `cbILHeader` IL 標頭中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="34d92-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="34d92-112">備註</span><span class="sxs-lookup"><span data-stu-id="34d92-112">Remarks</span></span>  

<span data-ttu-id="34d92-113">每當以 JIT 方式編譯動態方法時，就會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="34d92-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="34d92-114">這包括各種 IL 存根和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="34d92-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="34d92-115">其目標是要為 profiler 寫入器提供足夠的資訊，以識別已編譯的方法給使用者。</span><span class="sxs-lookup"><span data-stu-id="34d92-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="34d92-116">`functionId` 因為動態方法沒有中繼資料，所以無法使用值解析其元資料標記。</span><span class="sxs-lookup"><span data-stu-id="34d92-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="34d92-117">`pILHeader`指標只在回呼期間有效。</span><span class="sxs-lookup"><span data-stu-id="34d92-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="34d92-118">需求</span><span class="sxs-lookup"><span data-stu-id="34d92-118">Requirements</span></span>  

 <span data-ttu-id="34d92-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34d92-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34d92-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34d92-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34d92-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34d92-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34d92-122">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34d92-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d92-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34d92-123">See also</span></span>

- [<span data-ttu-id="34d92-124">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="34d92-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="34d92-125">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="34d92-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
