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
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498995"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="41dca-102">ICorProfilerCallback8：:D ynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="41dca-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="41dca-103">[在 .NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="41dca-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="41dca-104">每當動態方法的 JIT 編譯開始時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="41dca-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41dca-105">語法</span><span class="sxs-lookup"><span data-stu-id="41dca-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41dca-106">參數</span><span class="sxs-lookup"><span data-stu-id="41dca-106">Parameters</span></span>  
<span data-ttu-id="41dca-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="41dca-107">[in] `functionId`</span></span>  
<span data-ttu-id="41dca-108">啟動 JIT 編譯之記憶體中函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="41dca-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="41dca-109">[in] `fIsSafeToBlock` 
 `true`若要指出封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回，`false`表示封鎖不會影響執行時間的作業。</span><span class="sxs-lookup"><span data-stu-id="41dca-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="41dca-110">[in] `pILHeader`方法的 IL 標頭的第一個位元組指標。</span><span class="sxs-lookup"><span data-stu-id="41dca-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="41dca-111">[in] `cbILHeader`IL 標頭中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="41dca-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="41dca-112">備註</span><span class="sxs-lookup"><span data-stu-id="41dca-112">Remarks</span></span>  

<span data-ttu-id="41dca-113">每當動態方法是 JIT 編譯時，就會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="41dca-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="41dca-114">這包括各種 IL stub 和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="41dca-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="41dca-115">其目標是要為 profiler 寫入器提供足夠的資訊，以向使用者識別已編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="41dca-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="41dca-116">`functionId`值無法用來解析其元資料標記，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="41dca-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="41dca-117">`pILHeader`只有在回呼期間，指標才有效。</span><span class="sxs-lookup"><span data-stu-id="41dca-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="41dca-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="41dca-118">Requirements</span></span>  
 <span data-ttu-id="41dca-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41dca-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41dca-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41dca-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41dca-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41dca-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41dca-122">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="41dca-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dca-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41dca-123">See also</span></span>

- [<span data-ttu-id="41dca-124">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="41dca-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="41dca-125">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="41dca-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
