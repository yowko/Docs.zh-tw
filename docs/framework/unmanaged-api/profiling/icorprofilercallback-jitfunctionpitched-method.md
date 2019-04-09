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
ms.openlocfilehash: c8aa46e869d50fc7aa65c1d4244ad4ff71657bad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186390"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="5ffb5-102">ICorProfilerCallback::JITFunctionPitched 方法</span><span class="sxs-lookup"><span data-stu-id="5ffb5-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="5ffb5-103">通知分析工具，已在 just-in-time (JIT) 的函式-編譯已從記憶體中移除。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ffb5-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ffb5-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ffb5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5ffb5-106">[in]已移除函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ffb5-107">備註</span><span class="sxs-lookup"><span data-stu-id="5ffb5-107">Remarks</span></span>  
 <span data-ttu-id="5ffb5-108">如果已移除的函式呼叫時，分析工具就會收到新的 JIT 編譯事件時重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="5ffb5-109">目前，common language runtime (CLR) JIT 編譯器不會移除函式的記憶體，因此此回呼中目前未使用，並分析工具將不會接收。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="5ffb5-110">值`functionId`無效，直到重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="5ffb5-111">重新編譯函式時，相同`functionId`將使用的值。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffb5-112">需求</span><span class="sxs-lookup"><span data-stu-id="5ffb5-112">Requirements</span></span>  
 <span data-ttu-id="5ffb5-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ffb5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffb5-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ffb5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ffb5-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ffb5-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5ffb5-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5ffb5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ffb5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ffb5-117">See also</span></span>

- [<span data-ttu-id="5ffb5-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5ffb5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
