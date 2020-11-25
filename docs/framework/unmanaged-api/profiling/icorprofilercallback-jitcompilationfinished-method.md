---
title: ICorProfilerCallback::JITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 98e81d2d02a9495b678d49fb916f99068dd604f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725530"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="38d8c-102">ICorProfilerCallback::JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="38d8c-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>

<span data-ttu-id="38d8c-103">通知分析工具，及時 (JIT) 編譯器已完成函式的編譯。</span><span class="sxs-lookup"><span data-stu-id="38d8c-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d8c-104">語法</span><span class="sxs-lookup"><span data-stu-id="38d8c-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38d8c-105">參數</span><span class="sxs-lookup"><span data-stu-id="38d8c-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="38d8c-106">\[in] 編譯的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="38d8c-106">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="38d8c-107">\[in] 表示編譯是否成功的值。</span><span class="sxs-lookup"><span data-stu-id="38d8c-107">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="38d8c-108">\[in] 值，指出封鎖程式是否會影響執行時間的操作。</span><span class="sxs-lookup"><span data-stu-id="38d8c-108">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="38d8c-109">`true`如果封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回，則值為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="38d8c-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="38d8c-110">雖然的值 `true` 不會危害執行時間，但它可能會扭曲分析結果。</span><span class="sxs-lookup"><span data-stu-id="38d8c-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="38d8c-111">需求</span><span class="sxs-lookup"><span data-stu-id="38d8c-111">Requirements</span></span>  

 <span data-ttu-id="38d8c-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38d8c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d8c-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38d8c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38d8c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38d8c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38d8c-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d8c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d8c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38d8c-116">See also</span></span>

- [<span data-ttu-id="38d8c-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="38d8c-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="38d8c-118">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="38d8c-118">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
