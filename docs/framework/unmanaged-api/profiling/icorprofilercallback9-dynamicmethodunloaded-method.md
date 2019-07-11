---
title: ICorProfilerCallback9::DynamicMethodUnloaded 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 680bd351a64632e67432ee03352ee7caa8f4b2d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780380"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="c1006-102">ICorProfilerCallback9::DynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="c1006-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="c1006-103">[.NET Framework 4.7.2 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="c1006-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="c1006-104">記憶體回收，並接著卸載動態方法時，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="c1006-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1006-105">語法</span><span class="sxs-lookup"><span data-stu-id="c1006-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1006-106">參數</span><span class="sxs-lookup"><span data-stu-id="c1006-106">Parameters</span></span>  
<span data-ttu-id="c1006-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="c1006-107">[in] `functionId`</span></span>  
<span data-ttu-id="c1006-108">記憶體中函式已被記憶體回收，並卸載的識別項。</span><span class="sxs-lookup"><span data-stu-id="c1006-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="c1006-109">需求</span><span class="sxs-lookup"><span data-stu-id="c1006-109">Requirements</span></span>  
 <span data-ttu-id="c1006-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1006-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1006-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1006-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1006-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1006-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1006-113">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c1006-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1006-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1006-114">See also</span></span>

- [<span data-ttu-id="c1006-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="c1006-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="c1006-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="c1006-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="c1006-117">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="c1006-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="c1006-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="c1006-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
