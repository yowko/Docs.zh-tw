---
title: ICorProfilerCallback::AssemblyUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 0a677e33950f178b916a5e9e9cbb7bd918c1349b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866607"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="b1d72-102">ICorProfilerCallback::AssemblyUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="b1d72-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="b1d72-103">通知分析工具元件正在卸載。</span><span class="sxs-lookup"><span data-stu-id="b1d72-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d72-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1d72-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1d72-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1d72-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="b1d72-106">中的 \[] 可識別正在卸載的元件。</span><span class="sxs-lookup"><span data-stu-id="b1d72-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1d72-107">備註</span><span class="sxs-lookup"><span data-stu-id="b1d72-107">Remarks</span></span>  
 <span data-ttu-id="b1d72-108">`AssemblyUnloadStarted` 方法傳回之後，`assemblyId` 的值對資訊要求無效，這是分析工具的最後機會取得此元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b1d72-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d72-109">需求</span><span class="sxs-lookup"><span data-stu-id="b1d72-109">Requirements</span></span>  
 <span data-ttu-id="b1d72-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1d72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d72-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1d72-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1d72-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1d72-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1d72-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d72-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d72-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d72-114">See also</span></span>

- [<span data-ttu-id="b1d72-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b1d72-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b1d72-116">AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b1d72-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
