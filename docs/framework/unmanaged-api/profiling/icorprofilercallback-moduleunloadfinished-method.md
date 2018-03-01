---
title: "ICorProfilerCallback::ModuleUnloadFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6f9f048d60d2d463e3d846fadda91932a9a2a091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="65d30-102">ICorProfilerCallback::ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="65d30-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="65d30-103">通知分析工具模組已卸載完成。</span><span class="sxs-lookup"><span data-stu-id="65d30-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d30-104">語法</span><span class="sxs-lookup"><span data-stu-id="65d30-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65d30-105">參數</span><span class="sxs-lookup"><span data-stu-id="65d30-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="65d30-106">[in]模組已卸載的識別碼。</span><span class="sxs-lookup"><span data-stu-id="65d30-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="65d30-107">[in]HRESULT，指出是否在模組已卸載成功。</span><span class="sxs-lookup"><span data-stu-id="65d30-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65d30-108">備註</span><span class="sxs-lookup"><span data-stu-id="65d30-108">Remarks</span></span>  
 <span data-ttu-id="65d30-109">值`moduleId`不正確資訊要求之後[icorprofilercallback:: Moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="65d30-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="65d30-110">卸載的類別的某些部分可能會繼續之後`ModuleUnloadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="65d30-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="65d30-111">失敗的 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="65d30-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="65d30-112">不過，成功 HRESULT 中`hrStatus`只會指出已成功卸載此模組的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="65d30-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d30-113">需求</span><span class="sxs-lookup"><span data-stu-id="65d30-113">Requirements</span></span>  
 <span data-ttu-id="65d30-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65d30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d30-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65d30-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65d30-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65d30-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65d30-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d30-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="65d30-118">See Also</span></span>  
 [<span data-ttu-id="65d30-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="65d30-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
