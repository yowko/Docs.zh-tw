---
title: "ICorProfilerCallback::ModuleLoadStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f88b2a287eef0bf3fe8edeba4b76a3b3a1ce4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="d0ca9-102">ICorProfilerCallback::ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d0ca9-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="d0ca9-103">通知分析工具已載入模組。</span><span class="sxs-lookup"><span data-stu-id="d0ca9-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ca9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0ca9-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0ca9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0ca9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d0ca9-106">[in]正在載入的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="d0ca9-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0ca9-107">備註</span><span class="sxs-lookup"><span data-stu-id="d0ca9-107">Remarks</span></span>  
 <span data-ttu-id="d0ca9-108">值`moduleId`不正確的資訊要求，直到[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0ca9-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ca9-109">需求</span><span class="sxs-lookup"><span data-stu-id="d0ca9-109">Requirements</span></span>  
 <span data-ttu-id="d0ca9-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0ca9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ca9-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0ca9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0ca9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0ca9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0ca9-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ca9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ca9-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0ca9-114">See Also</span></span>  
 [<span data-ttu-id="d0ca9-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d0ca9-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
