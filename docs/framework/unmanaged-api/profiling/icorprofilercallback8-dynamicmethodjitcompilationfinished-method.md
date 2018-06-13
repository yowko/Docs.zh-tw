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
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454993"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="9be10-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9be10-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="9be10-103">[在.NET Framework 4.7 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="9be10-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="9be10-104">完成動態方法的 JIT 編譯時，通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="9be10-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be10-105">語法</span><span class="sxs-lookup"><span data-stu-id="9be10-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9be10-106">參數</span><span class="sxs-lookup"><span data-stu-id="9be10-106">Parameters</span></span>  
<span data-ttu-id="9be10-107">[輸入] `functionId`</span><span class="sxs-lookup"><span data-stu-id="9be10-107">[in] `functionId`</span></span>  
<span data-ttu-id="9be10-108">記憶體中函式的 JIT 編譯為已啟動的識別項。</span><span class="sxs-lookup"><span data-stu-id="9be10-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="9be10-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="9be10-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="9be10-110">值，指出 JIT 編譯是否成功。</span><span class="sxs-lookup"><span data-stu-id="9be10-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="9be10-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="9be10-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="9be10-112">`true` 表示封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候`false`表示封鎖將不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="9be10-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="9be10-113">備註</span><span class="sxs-lookup"><span data-stu-id="9be10-113">Remarks</span></span>  

<span data-ttu-id="9be10-114">動態方法的 JIT 編譯完成時會觸發此回呼。</span><span class="sxs-lookup"><span data-stu-id="9be10-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="9be10-115">這包括各種 IL 虛設常式和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="9be10-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="9be10-116">其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。</span><span class="sxs-lookup"><span data-stu-id="9be10-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="9be10-117">`functionId` 無法解析的中繼資料語彙基元，為使用值，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9be10-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="9be10-118">需求</span><span class="sxs-lookup"><span data-stu-id="9be10-118">Requirements</span></span>  
 <span data-ttu-id="9be10-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9be10-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be10-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9be10-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9be10-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9be10-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9be10-122">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9be10-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be10-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9be10-123">See Also</span></span>  
 [<span data-ttu-id="9be10-124">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="9be10-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [<span data-ttu-id="9be10-125">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="9be10-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
