---
title: ICorProfilerCallback::ModuleUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb00a56b0d80b78867f70e64c1c9bdf0fc49e1be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041934"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="fc208-102">ICorProfilerCallback::ModuleUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="fc208-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="fc208-103">通知分析工具正在卸載模組。</span><span class="sxs-lookup"><span data-stu-id="fc208-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc208-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc208-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fc208-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc208-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="fc208-106">[in]正在卸載模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc208-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc208-107">備註</span><span class="sxs-lookup"><span data-stu-id="fc208-107">Remarks</span></span>  
 <span data-ttu-id="fc208-108">值`moduleId`不是有效資訊要求之後`ModuleUnloadStarted`方法會傳回 — 這是分析工具的最後機會，以取得此模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fc208-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc208-109">需求</span><span class="sxs-lookup"><span data-stu-id="fc208-109">Requirements</span></span>  
 <span data-ttu-id="fc208-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc208-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc208-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc208-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc208-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc208-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc208-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc208-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc208-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc208-114">See also</span></span>

- [<span data-ttu-id="fc208-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fc208-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="fc208-116">ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fc208-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
