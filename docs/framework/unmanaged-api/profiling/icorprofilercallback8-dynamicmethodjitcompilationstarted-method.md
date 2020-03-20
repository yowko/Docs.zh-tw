---
title: ICorProfiler回檔8：:DynamicMethodJIT編譯啟動方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177042"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="b474c-102">ICorProfiler回檔8：:DynamicMethodJIT編譯啟動方法</span><span class="sxs-lookup"><span data-stu-id="b474c-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="b474c-103">[在 .NET 框架 4.7 和更高版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b474c-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="b474c-104">每當開始動態方法的 JIT 編譯時，通知探測器。</span><span class="sxs-lookup"><span data-stu-id="b474c-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b474c-105">語法</span><span class="sxs-lookup"><span data-stu-id="b474c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b474c-106">參數</span><span class="sxs-lookup"><span data-stu-id="b474c-106">Parameters</span></span>  
<span data-ttu-id="b474c-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="b474c-107">[in] `functionId`</span></span>  
<span data-ttu-id="b474c-108">啟動 JIT 編譯的記憶體中函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b474c-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="b474c-109">[在]`fIsSafeToBlock`指示阻塞可能導致運行時等待調用執行緒從此回檔
`true`返回;`false`指示阻塞不會影響運行時的操作。</span><span class="sxs-lookup"><span data-stu-id="b474c-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="b474c-110">[在]`pILHeader`指向方法 IL 標頭的第一個位元組的指標。</span><span class="sxs-lookup"><span data-stu-id="b474c-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="b474c-111">[在]`cbILHeader` IL 標頭中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="b474c-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="b474c-112">備註</span><span class="sxs-lookup"><span data-stu-id="b474c-112">Remarks</span></span>  

<span data-ttu-id="b474c-113">每當編譯動態方法時，就會觸發此回檔。</span><span class="sxs-lookup"><span data-stu-id="b474c-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="b474c-114">這包括各種 IL 存根和 LCG 方法。</span><span class="sxs-lookup"><span data-stu-id="b474c-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="b474c-115">其目的是向探測器編寫器提供足夠的資訊，以便向使用者標識編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="b474c-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="b474c-116">`functionId`值不能用於解析到其中繼資料權杖，因為動態方法沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b474c-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="b474c-117">指標`pILHeader`僅在回檔期間有效。</span><span class="sxs-lookup"><span data-stu-id="b474c-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="b474c-118">需求</span><span class="sxs-lookup"><span data-stu-id="b474c-118">Requirements</span></span>  
 <span data-ttu-id="b474c-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b474c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b474c-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b474c-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b474c-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b474c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b474c-122">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b474c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b474c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b474c-123">See also</span></span>

- [<span data-ttu-id="b474c-124">DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b474c-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="b474c-125">ICorProfilerCallback8 介面</span><span class="sxs-lookup"><span data-stu-id="b474c-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
