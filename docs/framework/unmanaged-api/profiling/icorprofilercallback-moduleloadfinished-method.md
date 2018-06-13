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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14f918a312031359043076be0b739f9b7e0e9f2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451639"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="411e6-102">ICorProfilerCallback::ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="411e6-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="411e6-103">通知分析工具已完成載入模組。</span><span class="sxs-lookup"><span data-stu-id="411e6-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="411e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="411e6-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="411e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="411e6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="411e6-106">[in]已完成載入的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="411e6-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="411e6-107">[in]HRESULT，指出是否已成功載入的模組。</span><span class="sxs-lookup"><span data-stu-id="411e6-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="411e6-108">備註</span><span class="sxs-lookup"><span data-stu-id="411e6-108">Remarks</span></span>  
 <span data-ttu-id="411e6-109">值`moduleId`不正確的資訊要求，直到`ModuleLoadFinished`方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="411e6-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="411e6-110">載入模組的某些部分可能會繼續之後`ModuleLoadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="411e6-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="411e6-111">失敗的 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="411e6-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="411e6-112">不過，成功 HRESULT 中`hrStatus`只會指出已成功載入模組的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="411e6-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="411e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="411e6-113">Requirements</span></span>  
 <span data-ttu-id="411e6-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="411e6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="411e6-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="411e6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="411e6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="411e6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="411e6-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="411e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411e6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="411e6-118">See Also</span></span>  
 [<span data-ttu-id="411e6-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="411e6-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="411e6-120">ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="411e6-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
