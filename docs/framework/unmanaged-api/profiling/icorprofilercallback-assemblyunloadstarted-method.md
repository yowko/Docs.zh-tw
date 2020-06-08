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
ms.openlocfilehash: 80054a8292c69b957664cb3573b0a8694c7f9fd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500399"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="98cb2-102">ICorProfilerCallback::AssemblyUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="98cb2-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="98cb2-103">通知分析工具元件正在卸載。</span><span class="sxs-lookup"><span data-stu-id="98cb2-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="98cb2-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98cb2-105">參數</span><span class="sxs-lookup"><span data-stu-id="98cb2-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="98cb2-106">\[在中，識別要卸載的元件。</span><span class="sxs-lookup"><span data-stu-id="98cb2-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="98cb2-107">備註</span><span class="sxs-lookup"><span data-stu-id="98cb2-107">Remarks</span></span>  
 <span data-ttu-id="98cb2-108">在方法傳回之後，的值 `assemblyId` 對資訊要求無效 `AssemblyUnloadStarted` ，這是分析工具的最後機會取得此元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="98cb2-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98cb2-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="98cb2-109">Requirements</span></span>  
 <span data-ttu-id="98cb2-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98cb2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98cb2-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98cb2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98cb2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98cb2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98cb2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98cb2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cb2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98cb2-114">See also</span></span>

- [<span data-ttu-id="98cb2-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="98cb2-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="98cb2-116">AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="98cb2-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
