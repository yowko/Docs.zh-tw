---
title: ICorProfilerCallback4::GetReJITParameters 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: d81d7275d197de1dfc99b135377459f509c2651f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439446"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="3a9c5-102">ICorProfilerCallback4::GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="3a9c5-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="3a9c5-103">可讓程式碼分析工具針對新重新編譯的方法主體，設定替代的程式碼產生旗標。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a9c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a9c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a9c5-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3a9c5-106">在包含 CLR 需要 JIT 重新編譯參數之方法的模組。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="3a9c5-107">在CLR 需要 JIT 重新編譯參數之方法的 `MethodDef`。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="3a9c5-108">在[ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)介面的指標，分析工具可用來為重新編譯的方法提供 JIT 重新編譯資訊。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a9c5-109">備註</span><span class="sxs-lookup"><span data-stu-id="3a9c5-109">Remarks</span></span>  
 <span data-ttu-id="3a9c5-110">CLR 會發出 `GetReJITParameters` 回呼，讓分析工具可以指定參數來重新編譯指定的方法。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="3a9c5-111">每個函式只會發出一次 `GetReJITParameters` 回呼;profiler 所提供的參數會套用至該函式的所有實例。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a9c5-112">需求</span><span class="sxs-lookup"><span data-stu-id="3a9c5-112">Requirements</span></span>  
 <span data-ttu-id="3a9c5-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a9c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a9c5-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a9c5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a9c5-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a9c5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a9c5-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a9c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9c5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a9c5-117">See also</span></span>

- [<span data-ttu-id="3a9c5-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3a9c5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="3a9c5-119">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="3a9c5-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="3a9c5-120">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="3a9c5-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="3a9c5-121">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="3a9c5-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
