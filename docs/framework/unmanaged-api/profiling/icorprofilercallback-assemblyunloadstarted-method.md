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
ms.openlocfilehash: bb7dade1ccd46cb9e13d45468c2ca2a8b451b70b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700297"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="cb8fc-102">ICorProfilerCallback::AssemblyUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="cb8fc-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="cb8fc-103">通知分析工具元件正在卸載。</span><span class="sxs-lookup"><span data-stu-id="cb8fc-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb8fc-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb8fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb8fc-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="cb8fc-106">\[in] 識別正在卸載的元件。</span><span class="sxs-lookup"><span data-stu-id="cb8fc-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb8fc-107">備註</span><span class="sxs-lookup"><span data-stu-id="cb8fc-107">Remarks</span></span>  

 <span data-ttu-id="cb8fc-108">在方法傳回之後，的值對 `assemblyId` 資訊要求而言是不正確 `AssemblyUnloadStarted` ，這是 profiler 取得此元件相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="cb8fc-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb8fc-109">需求</span><span class="sxs-lookup"><span data-stu-id="cb8fc-109">Requirements</span></span>  

 <span data-ttu-id="cb8fc-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb8fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8fc-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb8fc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb8fc-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb8fc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb8fc-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb8fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8fc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb8fc-114">See also</span></span>

- [<span data-ttu-id="cb8fc-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cb8fc-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cb8fc-116">AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="cb8fc-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
