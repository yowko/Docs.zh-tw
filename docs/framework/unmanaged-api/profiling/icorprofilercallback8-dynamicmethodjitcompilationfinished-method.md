---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba9f9d4ee5f95def3dcd2d757517e225c826cb9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757998"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="a09f1-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="a09f1-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="a09f1-103">[.NET Framework 4.7 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="a09f1-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a09f1-104">通知分析工具，每當完成動態方法的 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="a09f1-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09f1-105">語法</span><span class="sxs-lookup"><span data-stu-id="a09f1-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a09f1-106">參數</span><span class="sxs-lookup"><span data-stu-id="a09f1-106">Parameters</span></span>  
<span data-ttu-id="a09f1-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a09f1-107">[in] `functionId`</span></span>  
<span data-ttu-id="a09f1-108">記憶體中函式開始的 JIT 編譯的識別項。</span><span class="sxs-lookup"><span data-stu-id="a09f1-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="a09f1-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="a09f1-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="a09f1-110">值，指出 JIT 編譯是否成功。</span><span class="sxs-lookup"><span data-stu-id="a09f1-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="a09f1-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="a09f1-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="a09f1-112">`true` 表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="a09f1-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="a09f1-113">備註</span><span class="sxs-lookup"><span data-stu-id="a09f1-113">Remarks</span></span>  

<span data-ttu-id="a09f1-114">JIT 編譯的動態方法已完成時會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="a09f1-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="a09f1-115">這包括各種 IL 虛設常式和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="a09f1-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a09f1-116">其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。</span><span class="sxs-lookup"><span data-stu-id="a09f1-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a09f1-117">`functionId` 無法解析為其中繼資料語彙基元中，使用值，因為動態方法有沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a09f1-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="a09f1-118">需求</span><span class="sxs-lookup"><span data-stu-id="a09f1-118">Requirements</span></span>  
 <span data-ttu-id="a09f1-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a09f1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09f1-120">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a09f1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a09f1-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a09f1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a09f1-122">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a09f1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09f1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a09f1-123">See also</span></span>

- [<span data-ttu-id="a09f1-124">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a09f1-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="a09f1-125">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="a09f1-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
