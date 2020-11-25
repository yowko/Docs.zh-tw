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
ms.openlocfilehash: 3f2b4a64b3f17b043f193e054c56601d706a10e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700375"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="0490b-102">ICorProfilerCallback::AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="0490b-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>

<span data-ttu-id="0490b-103">通知分析工具元件已卸載。</span><span class="sxs-lookup"><span data-stu-id="0490b-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0490b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0490b-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0490b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0490b-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="0490b-106">\[in] 識別正在卸載的元件。</span><span class="sxs-lookup"><span data-stu-id="0490b-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="0490b-107">\[in] HRESULT，指出是否已成功卸載元件。</span><span class="sxs-lookup"><span data-stu-id="0490b-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="0490b-108">備註</span><span class="sxs-lookup"><span data-stu-id="0490b-108">Remarks</span></span>  

 <span data-ttu-id="0490b-109">在 `assemblyId` [ICorProfilerCallback：： AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) 方法傳回之後，的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="0490b-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="0490b-110">卸載元件的部分可能會在回呼之後繼續進行 `AssemblyUnloadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="0490b-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="0490b-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="0490b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="0490b-112">但是，中的成功 HRESULT `hrStatus` 只會指出卸載元件的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="0490b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0490b-113">需求</span><span class="sxs-lookup"><span data-stu-id="0490b-113">Requirements</span></span>  

 <span data-ttu-id="0490b-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0490b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0490b-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0490b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0490b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0490b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0490b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0490b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0490b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0490b-118">See also</span></span>

- [<span data-ttu-id="0490b-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0490b-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
