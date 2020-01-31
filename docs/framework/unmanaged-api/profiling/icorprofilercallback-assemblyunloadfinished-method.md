---
title: ICorProfilerCallback::AssemblyUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 734ae1d14d02d47c7d3126f1b4cf55dcb4ad151b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866620"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="33441-102">ICorProfilerCallback::AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="33441-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="33441-103">通知分析工具元件已卸載。</span><span class="sxs-lookup"><span data-stu-id="33441-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33441-104">語法</span><span class="sxs-lookup"><span data-stu-id="33441-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33441-105">參數</span><span class="sxs-lookup"><span data-stu-id="33441-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="33441-106">中的 \[] 可識別正在卸載的元件。</span><span class="sxs-lookup"><span data-stu-id="33441-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="33441-107">\[in]） HRESULT，指出元件是否已成功卸載。</span><span class="sxs-lookup"><span data-stu-id="33441-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="33441-108">備註</span><span class="sxs-lookup"><span data-stu-id="33441-108">Remarks</span></span>  
 <span data-ttu-id="33441-109">[ICorProfilerCallback：： AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md)方法傳回之後，`assemblyId` 的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="33441-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="33441-110">卸載元件的某些部分可能會在 `AssemblyUnloadFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="33441-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="33441-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="33441-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="33441-112">不過，`hrStatus` 中的成功 HRESULT 只會指出卸載元件的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="33441-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33441-113">需求</span><span class="sxs-lookup"><span data-stu-id="33441-113">Requirements</span></span>  
 <span data-ttu-id="33441-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33441-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33441-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33441-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33441-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33441-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33441-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33441-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33441-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="33441-118">See also</span></span>

- [<span data-ttu-id="33441-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="33441-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
