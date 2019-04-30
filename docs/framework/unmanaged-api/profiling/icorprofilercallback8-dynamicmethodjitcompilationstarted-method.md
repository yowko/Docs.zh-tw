---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4b8bffeb71497a7dd8e2ed25b833f9216d8017e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049735"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="a1c1d-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a1c1d-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="a1c1d-103">[.NET Framework 4.7 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="a1c1d-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a1c1d-104">已啟動的動態方法的 JIT 編譯時，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c1d-105">語法</span><span class="sxs-lookup"><span data-stu-id="a1c1d-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1c1d-106">參數</span><span class="sxs-lookup"><span data-stu-id="a1c1d-106">Parameters</span></span>  
<span data-ttu-id="a1c1d-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a1c1d-107">[in] `functionId`</span></span>  
<span data-ttu-id="a1c1d-108">記憶體中函式開始的 JIT 編譯的識別項。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="a1c1d-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="a1c1d-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="a1c1d-110">`true` 表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="a1c1d-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="a1c1d-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="a1c1d-112">方法的 IL 標頭的第一個位元組指標。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="a1c1d-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="a1c1d-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="a1c1d-114">IL 標頭中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="a1c1d-115">備註</span><span class="sxs-lookup"><span data-stu-id="a1c1d-115">Remarks</span></span>  

<span data-ttu-id="a1c1d-116">動態方法可讓您在 JIT 編譯時，就會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="a1c1d-117">這包括各種 IL 虛設常式和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a1c1d-118">其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a1c1d-119">`functionId` 無法解析為其中繼資料語彙基元中，使用值，因為動態方法有沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="a1c1d-120">`pILHeader`指標才會有效的回呼期間。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1c1d-121">需求</span><span class="sxs-lookup"><span data-stu-id="a1c1d-121">Requirements</span></span>  
 <span data-ttu-id="a1c1d-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c1d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1c1d-123">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1c1d-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1c1d-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1c1d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1c1d-125">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a1c1d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c1d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1c1d-126">See also</span></span>

- [<span data-ttu-id="a1c1d-127">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="a1c1d-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="a1c1d-128">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="a1c1d-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
