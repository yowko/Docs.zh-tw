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
ms.openlocfilehash: 2cee763674da7472ca48355e7eaba3b7dfb7adbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730301"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="180b5-102">ICorProfilerCallback4::GetReJITParameters 方法</span><span class="sxs-lookup"><span data-stu-id="180b5-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>

<span data-ttu-id="180b5-103">允許程式碼分析工具為新重新編譯的方法主體設定替代程式碼產生旗標。</span><span class="sxs-lookup"><span data-stu-id="180b5-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="180b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="180b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="180b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="180b5-105">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="180b5-106">在包含 CLR 需要 JIT 重新編譯參數之方法的模組。</span><span class="sxs-lookup"><span data-stu-id="180b5-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="180b5-107">在 `MethodDef` CLR 需要 JIT 重新編譯參數之方法的。</span><span class="sxs-lookup"><span data-stu-id="180b5-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="180b5-108">在 [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) 介面的指標，分析工具可以使用它來提供重新編譯之方法的 JIT 重新編譯資訊。</span><span class="sxs-lookup"><span data-stu-id="180b5-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="180b5-109">備註</span><span class="sxs-lookup"><span data-stu-id="180b5-109">Remarks</span></span>  

 <span data-ttu-id="180b5-110">CLR 會發出回呼，讓分析工具 `GetReJITParameters` 可以指定參數來重新編譯指定的方法。</span><span class="sxs-lookup"><span data-stu-id="180b5-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="180b5-111">`GetReJITParameters`回呼只會針對每個函式發出一次; profiler 提供的參數會套用至該函式的所有實例。</span><span class="sxs-lookup"><span data-stu-id="180b5-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="180b5-112">需求</span><span class="sxs-lookup"><span data-stu-id="180b5-112">Requirements</span></span>  

 <span data-ttu-id="180b5-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="180b5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="180b5-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="180b5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="180b5-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="180b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="180b5-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="180b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180b5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="180b5-117">See also</span></span>

- [<span data-ttu-id="180b5-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="180b5-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="180b5-119">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="180b5-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="180b5-120">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="180b5-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="180b5-121">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="180b5-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
