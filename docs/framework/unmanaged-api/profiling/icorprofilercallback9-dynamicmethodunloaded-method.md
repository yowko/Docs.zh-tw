---
title: ICorProfiler回撥9：:Dynamic方法未載入方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177029"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="b3830-102">ICorProfiler回撥9：:Dynamic方法未載入方法</span><span class="sxs-lookup"><span data-stu-id="b3830-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="b3830-103">[在 .NET 框架 4.7.2 和更高版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b3830-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="b3830-104">每當收集動態方法並隨後卸載時，通知探測器。</span><span class="sxs-lookup"><span data-stu-id="b3830-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3830-105">語法</span><span class="sxs-lookup"><span data-stu-id="b3830-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3830-106">參數</span><span class="sxs-lookup"><span data-stu-id="b3830-106">Parameters</span></span>  
<span data-ttu-id="b3830-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="b3830-107">[in] `functionId`</span></span>  
<span data-ttu-id="b3830-108">已垃圾回收和卸載的記憶體中函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b3830-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3830-109">需求</span><span class="sxs-lookup"><span data-stu-id="b3830-109">Requirements</span></span>  
 <span data-ttu-id="b3830-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3830-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3830-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3830-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3830-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3830-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3830-113">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b3830-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3830-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3830-114">See also</span></span>

- [<span data-ttu-id="b3830-115">ICorProfiler回檔8.動態方法JIT編譯啟動方法</span><span class="sxs-lookup"><span data-stu-id="b3830-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="b3830-116">ICorProfiler回檔8.動態方法JIT編譯完成方法</span><span class="sxs-lookup"><span data-stu-id="b3830-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="b3830-117">ICorProfilerCallback9 介面</span><span class="sxs-lookup"><span data-stu-id="b3830-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="b3830-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="b3830-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
