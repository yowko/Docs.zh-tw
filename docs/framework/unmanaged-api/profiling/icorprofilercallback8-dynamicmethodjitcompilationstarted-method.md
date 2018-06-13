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
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454746"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="549c7-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="549c7-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="549c7-103">[在.NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="549c7-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="549c7-104">動態方法的 JIT 編譯已啟動時，通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="549c7-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="549c7-105">語法</span><span class="sxs-lookup"><span data-stu-id="549c7-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="549c7-106">參數</span><span class="sxs-lookup"><span data-stu-id="549c7-106">Parameters</span></span>  
<span data-ttu-id="549c7-107">[輸入] `functionId`</span><span class="sxs-lookup"><span data-stu-id="549c7-107">[in] `functionId`</span></span>  
<span data-ttu-id="549c7-108">記憶體中函式的 JIT 編譯為已啟動的識別項。</span><span class="sxs-lookup"><span data-stu-id="549c7-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="549c7-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="549c7-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="549c7-110">`true` 表示封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候`false`表示封鎖將不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="549c7-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="549c7-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="549c7-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="549c7-112">方法的 IL 標頭的第一個位元組指標。</span><span class="sxs-lookup"><span data-stu-id="549c7-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="549c7-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="549c7-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="549c7-114">IL 標頭中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="549c7-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="549c7-115">備註</span><span class="sxs-lookup"><span data-stu-id="549c7-115">Remarks</span></span>  

<span data-ttu-id="549c7-116">動態方法可讓您在 JIT 編譯時會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="549c7-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="549c7-117">這包括各種 IL 虛設常式和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="549c7-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="549c7-118">其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。</span><span class="sxs-lookup"><span data-stu-id="549c7-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="549c7-119">`functionId` 無法解析的中繼資料語彙基元，為使用值，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="549c7-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="549c7-120">`pILHeader`指標只適用於回呼期間。</span><span class="sxs-lookup"><span data-stu-id="549c7-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="549c7-121">需求</span><span class="sxs-lookup"><span data-stu-id="549c7-121">Requirements</span></span>  
 <span data-ttu-id="549c7-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="549c7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="549c7-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="549c7-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="549c7-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="549c7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="549c7-125">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="549c7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549c7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="549c7-126">See Also</span></span>  
 [<span data-ttu-id="549c7-127">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="549c7-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [<span data-ttu-id="549c7-128">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="549c7-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
