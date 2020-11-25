---
title: ICorProfilerCallback9：:D ynamicMethodUnloaded 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e6fe3430696c16405d4ae414436bb12882c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732344"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="509be-102">ICorProfilerCallback9：:D ynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="509be-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="509be-103">[在 .NET Framework 4.7.2 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="509be-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="509be-104">每當有垃圾收集動態方法，並隨後卸載時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="509be-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="509be-105">語法</span><span class="sxs-lookup"><span data-stu-id="509be-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="509be-106">參數</span><span class="sxs-lookup"><span data-stu-id="509be-106">Parameters</span></span>  

<span data-ttu-id="509be-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="509be-107">[in] `functionId`</span></span>  
<span data-ttu-id="509be-108">已進行垃圾收集和卸載的記憶體中函數識別碼。</span><span class="sxs-lookup"><span data-stu-id="509be-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="509be-109">需求</span><span class="sxs-lookup"><span data-stu-id="509be-109">Requirements</span></span>  

 <span data-ttu-id="509be-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="509be-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="509be-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="509be-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="509be-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="509be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="509be-113">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="509be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="509be-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="509be-114">See also</span></span>

- [<span data-ttu-id="509be-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="509be-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="509be-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="509be-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="509be-117">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="509be-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="509be-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="509be-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
