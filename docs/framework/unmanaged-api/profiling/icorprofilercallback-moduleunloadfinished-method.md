---
title: ICorProfilerCallback::ModuleUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 40cb666c47c690dc930ec2cb7f6c89662464780e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445918"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="46580-102">ICorProfilerCallback::ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="46580-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="46580-103">Notifies the profiler that a module has finished unloading.</span><span class="sxs-lookup"><span data-stu-id="46580-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46580-104">語法</span><span class="sxs-lookup"><span data-stu-id="46580-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46580-105">參數</span><span class="sxs-lookup"><span data-stu-id="46580-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="46580-106">[in] The ID of the module that was unloaded.</span><span class="sxs-lookup"><span data-stu-id="46580-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="46580-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span><span class="sxs-lookup"><span data-stu-id="46580-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46580-108">備註</span><span class="sxs-lookup"><span data-stu-id="46580-108">Remarks</span></span>  
 <span data-ttu-id="46580-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span><span class="sxs-lookup"><span data-stu-id="46580-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="46580-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="46580-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="46580-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="46580-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="46580-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span><span class="sxs-lookup"><span data-stu-id="46580-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46580-113">需求</span><span class="sxs-lookup"><span data-stu-id="46580-113">Requirements</span></span>  
 <span data-ttu-id="46580-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46580-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46580-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46580-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46580-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46580-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46580-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46580-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46580-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="46580-118">See also</span></span>

- [<span data-ttu-id="46580-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="46580-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
