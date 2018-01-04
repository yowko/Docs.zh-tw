---
title: "ICorProfilerCallback::ModuleUnloadStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 384d655254cc79283f93ff2e608b0429c4a84ae8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="7fc9c-102">ICorProfilerCallback::ModuleUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7fc9c-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="7fc9c-103">通知分析工具正在卸載模組。</span><span class="sxs-lookup"><span data-stu-id="7fc9c-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fc9c-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7fc9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7fc9c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7fc9c-106">[in]正在解除載入的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="7fc9c-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fc9c-107">備註</span><span class="sxs-lookup"><span data-stu-id="7fc9c-107">Remarks</span></span>  
 <span data-ttu-id="7fc9c-108">值`moduleId`不正確資訊要求之後`ModuleUnloadStarted`方法會傳回-這是程式碼剖析工具以取得此模組的相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="7fc9c-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fc9c-109">需求</span><span class="sxs-lookup"><span data-stu-id="7fc9c-109">Requirements</span></span>  
 <span data-ttu-id="7fc9c-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7fc9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fc9c-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7fc9c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7fc9c-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fc9c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fc9c-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fc9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc9c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7fc9c-114">See Also</span></span>  
 [<span data-ttu-id="7fc9c-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7fc9c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7fc9c-116">ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7fc9c-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
