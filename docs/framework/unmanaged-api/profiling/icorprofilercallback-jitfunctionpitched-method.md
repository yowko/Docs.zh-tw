---
title: ICorProfilerCallback::JITFunctionPitched 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71df3bc707099cbad06742d964881ee629216b69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782810"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="95a53-102">ICorProfilerCallback::JITFunctionPitched 方法</span><span class="sxs-lookup"><span data-stu-id="95a53-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="95a53-103">通知分析工具，已在 just-in-time (JIT) 的函式-編譯已從記憶體中移除。</span><span class="sxs-lookup"><span data-stu-id="95a53-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a53-104">語法</span><span class="sxs-lookup"><span data-stu-id="95a53-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a53-105">參數</span><span class="sxs-lookup"><span data-stu-id="95a53-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="95a53-106">[in]已移除函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="95a53-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a53-107">備註</span><span class="sxs-lookup"><span data-stu-id="95a53-107">Remarks</span></span>  
 <span data-ttu-id="95a53-108">如果已移除的函式呼叫時，分析工具就會收到新的 JIT 編譯事件時重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="95a53-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="95a53-109">目前，common language runtime (CLR) JIT 編譯器不會移除函式的記憶體，因此此回呼中目前未使用，並分析工具將不會接收。</span><span class="sxs-lookup"><span data-stu-id="95a53-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="95a53-110">值`functionId`無效，直到重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="95a53-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="95a53-111">重新編譯函式時，相同`functionId`將使用的值。</span><span class="sxs-lookup"><span data-stu-id="95a53-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a53-112">需求</span><span class="sxs-lookup"><span data-stu-id="95a53-112">Requirements</span></span>  
 <span data-ttu-id="95a53-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95a53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a53-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95a53-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95a53-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95a53-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95a53-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a53-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95a53-117">See also</span></span>

- [<span data-ttu-id="95a53-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="95a53-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
