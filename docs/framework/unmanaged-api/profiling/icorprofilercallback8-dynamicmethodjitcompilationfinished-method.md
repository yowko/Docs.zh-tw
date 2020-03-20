---
title: ICorProfiler回檔8：:DynamicMethodJIT編譯完成方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175105"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="a22da-102">ICorProfiler回檔8：:DynamicMethodJIT編譯完成方法</span><span class="sxs-lookup"><span data-stu-id="a22da-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="a22da-103">[在 .NET 框架 4.7 和更高版本中支援]</span><span class="sxs-lookup"><span data-stu-id="a22da-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a22da-104">每當動態方法的 JIT 編譯完成時，通知探測器。</span><span class="sxs-lookup"><span data-stu-id="a22da-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22da-105">語法</span><span class="sxs-lookup"><span data-stu-id="a22da-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a22da-106">參數</span><span class="sxs-lookup"><span data-stu-id="a22da-106">Parameters</span></span>  
<span data-ttu-id="a22da-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a22da-107">[in] `functionId`</span></span>  
<span data-ttu-id="a22da-108">啟動 JIT 編譯的記憶體中函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a22da-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="a22da-109">[在]`hrStatus`指示 JIT 編譯是否成功的值。</span><span class="sxs-lookup"><span data-stu-id="a22da-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="a22da-110">[在]`fIsSafeToBlock`指示阻塞可能導致運行時等待調用執行緒從此回檔
`true`返回;`false`指示阻塞不會影響運行時的操作。</span><span class="sxs-lookup"><span data-stu-id="a22da-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="a22da-111">備註</span><span class="sxs-lookup"><span data-stu-id="a22da-111">Remarks</span></span>  

<span data-ttu-id="a22da-112">每當動態方法的 JIT 編譯完成時，都會觸發此回檔。</span><span class="sxs-lookup"><span data-stu-id="a22da-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="a22da-113">這包括各種 IL 存根和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="a22da-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a22da-114">其目的是向探測器編寫器提供足夠的資訊，以便向使用者標識編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="a22da-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a22da-115">`functionId`值不能用於解析到其中繼資料權杖，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a22da-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="a22da-116">需求</span><span class="sxs-lookup"><span data-stu-id="a22da-116">Requirements</span></span>  
 <span data-ttu-id="a22da-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a22da-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a22da-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a22da-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a22da-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a22da-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a22da-120">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a22da-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22da-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a22da-121">See also</span></span>

- [<span data-ttu-id="a22da-122">DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a22da-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="a22da-123">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="a22da-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
