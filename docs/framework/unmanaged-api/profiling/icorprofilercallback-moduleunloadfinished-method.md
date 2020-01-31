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
ms.openlocfilehash: b13573d19ab4d8bb655c1e153530dc70173abe82
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866139"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="87896-102">ICorProfilerCallback::ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="87896-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="87896-103">通知 profiler 模組已完成卸載。</span><span class="sxs-lookup"><span data-stu-id="87896-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87896-104">語法</span><span class="sxs-lookup"><span data-stu-id="87896-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87896-105">參數</span><span class="sxs-lookup"><span data-stu-id="87896-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="87896-106">在已卸載之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="87896-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="87896-107">在HRESULT，指出模組是否已成功卸載。</span><span class="sxs-lookup"><span data-stu-id="87896-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87896-108">備註</span><span class="sxs-lookup"><span data-stu-id="87896-108">Remarks</span></span>  
 <span data-ttu-id="87896-109">[ICorProfilerCallback：： ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md)方法傳回之後，`moduleId` 的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="87896-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="87896-110">卸載類別的某些部分可能會在 `ModuleUnloadFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="87896-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="87896-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="87896-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="87896-112">不過，`hrStatus` 中的成功 HRESULT 只會指出卸載模組的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="87896-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87896-113">需求</span><span class="sxs-lookup"><span data-stu-id="87896-113">Requirements</span></span>  
 <span data-ttu-id="87896-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87896-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87896-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87896-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87896-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87896-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87896-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87896-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87896-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="87896-118">See also</span></span>

- [<span data-ttu-id="87896-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="87896-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
