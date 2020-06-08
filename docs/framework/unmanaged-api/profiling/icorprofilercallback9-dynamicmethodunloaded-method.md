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
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498969"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="d0e2c-102">ICorProfilerCallback9：:D ynamicMethodUnloaded 方法</span><span class="sxs-lookup"><span data-stu-id="d0e2c-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="d0e2c-103">[在 .NET Framework 4.7.2 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="d0e2c-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="d0e2c-104">每當動態方法被垃圾收集並隨後卸載時，就會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="d0e2c-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e2c-105">語法</span><span class="sxs-lookup"><span data-stu-id="d0e2c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0e2c-106">參數</span><span class="sxs-lookup"><span data-stu-id="d0e2c-106">Parameters</span></span>  
<span data-ttu-id="d0e2c-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="d0e2c-107">[in] `functionId`</span></span>  
<span data-ttu-id="d0e2c-108">已進行垃圾收集和卸載的記憶體內建函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="d0e2c-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0e2c-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="d0e2c-109">Requirements</span></span>  
 <span data-ttu-id="d0e2c-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e2c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0e2c-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0e2c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0e2c-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0e2c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0e2c-113">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0e2c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e2c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e2c-114">See also</span></span>

- [<span data-ttu-id="d0e2c-115">ICorProfilerCallback8. DynamicMethodJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d0e2c-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="d0e2c-116">ICorProfilerCallback8. DynamicMethodJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="d0e2c-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="d0e2c-117">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="d0e2c-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="d0e2c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="d0e2c-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
