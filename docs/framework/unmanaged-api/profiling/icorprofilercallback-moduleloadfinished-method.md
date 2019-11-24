---
title: ICorProfilerCallback::ModuleLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 08fbf49e6944de4934a9fe7a960405ee96a7d8e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445934"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="ddc76-102">ICorProfilerCallback::ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="ddc76-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="ddc76-103">Notifies the profiler that a module has finished loading.</span><span class="sxs-lookup"><span data-stu-id="ddc76-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc76-104">語法</span><span class="sxs-lookup"><span data-stu-id="ddc76-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddc76-105">參數</span><span class="sxs-lookup"><span data-stu-id="ddc76-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ddc76-106">[in] The ID of the module that has finished loading.</span><span class="sxs-lookup"><span data-stu-id="ddc76-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ddc76-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span><span class="sxs-lookup"><span data-stu-id="ddc76-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddc76-108">備註</span><span class="sxs-lookup"><span data-stu-id="ddc76-108">Remarks</span></span>  
 <span data-ttu-id="ddc76-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="ddc76-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ddc76-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="ddc76-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="ddc76-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="ddc76-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ddc76-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span><span class="sxs-lookup"><span data-stu-id="ddc76-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc76-113">需求</span><span class="sxs-lookup"><span data-stu-id="ddc76-113">Requirements</span></span>  
 <span data-ttu-id="ddc76-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc76-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddc76-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddc76-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddc76-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddc76-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddc76-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddc76-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc76-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddc76-118">See also</span></span>

- [<span data-ttu-id="ddc76-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ddc76-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ddc76-120">ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="ddc76-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
