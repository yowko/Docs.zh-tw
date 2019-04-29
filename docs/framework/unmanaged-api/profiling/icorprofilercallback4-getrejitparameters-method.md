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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca176be93b92e44228d9b4063e87a62263e83e04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782502"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="f213e-102">ICorProfilerCallback4::GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="f213e-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="f213e-103">可讓程式碼剖析工具，來設定新的重新編譯的方法主體的替代程式碼產生旗標。</span><span class="sxs-lookup"><span data-stu-id="f213e-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f213e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f213e-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f213e-105">參數</span><span class="sxs-lookup"><span data-stu-id="f213e-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f213e-106">[in]包含 CLR 必須 JIT 重新編譯參數之方法的模組。</span><span class="sxs-lookup"><span data-stu-id="f213e-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="f213e-107">[in]`MethodDef` ，CLR 需要 JIT 重新編譯參數的方法。</span><span class="sxs-lookup"><span data-stu-id="f213e-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="f213e-108">[in]指標[ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)分析工具可用來提供方法重新編譯過的 JIT 重新編譯資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="f213e-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f213e-109">備註</span><span class="sxs-lookup"><span data-stu-id="f213e-109">Remarks</span></span>  
 <span data-ttu-id="f213e-110">CLR 問題`GetReJITParameters`回呼，讓分析工具指定重新編譯特定的方法的參數。</span><span class="sxs-lookup"><span data-stu-id="f213e-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="f213e-111">`GetReJITParameters`回呼發出一次，每個函式，分析工具所提供的參數適用於所有的執行個體，該函式。</span><span class="sxs-lookup"><span data-stu-id="f213e-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f213e-112">需求</span><span class="sxs-lookup"><span data-stu-id="f213e-112">Requirements</span></span>  
 <span data-ttu-id="f213e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f213e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f213e-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f213e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f213e-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f213e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f213e-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f213e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f213e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f213e-117">See also</span></span>

- [<span data-ttu-id="f213e-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f213e-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f213e-119">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="f213e-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="f213e-120">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f213e-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="f213e-121">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f213e-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
