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
ms.openlocfilehash: cf51d2a0e7381cd495da8f3846302ec806c34774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451408"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="a37d9-102">ICorProfilerCallback::JITFunctionPitched 方法</span><span class="sxs-lookup"><span data-stu-id="a37d9-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="a37d9-103">通知分析工具，已在 just-in-time (JIT) 的函式的編譯已從記憶體移除。</span><span class="sxs-lookup"><span data-stu-id="a37d9-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a37d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="a37d9-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a37d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="a37d9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a37d9-106">[in]已移除的函式 ID。</span><span class="sxs-lookup"><span data-stu-id="a37d9-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a37d9-107">備註</span><span class="sxs-lookup"><span data-stu-id="a37d9-107">Remarks</span></span>  
 <span data-ttu-id="a37d9-108">如果移除的函式呼叫時，分析工具會收到新的 JIT 編譯事件時重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="a37d9-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="a37d9-109">目前，common language runtime (CLR) JIT 編譯器不會移除函式的記憶體，因此這個回呼目前未使用和分析工具將不會接收。</span><span class="sxs-lookup"><span data-stu-id="a37d9-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="a37d9-110">值`functionId`無效，直到重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="a37d9-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="a37d9-111">重新編譯函式時，相同`functionId`將使用的值。</span><span class="sxs-lookup"><span data-stu-id="a37d9-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a37d9-112">需求</span><span class="sxs-lookup"><span data-stu-id="a37d9-112">Requirements</span></span>  
 <span data-ttu-id="a37d9-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a37d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a37d9-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a37d9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a37d9-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a37d9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a37d9-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a37d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37d9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a37d9-117">See Also</span></span>  
 [<span data-ttu-id="a37d9-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a37d9-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
