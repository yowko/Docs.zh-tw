---
title: ICorProfilerCallback::ModuleLoadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa5ca8871ab284d2a46e6777b226f5a9b155e566
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502465"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="a18ce-102">ICorProfilerCallback::ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a18ce-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="a18ce-103">通知分析工具載入的模組。</span><span class="sxs-lookup"><span data-stu-id="a18ce-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a18ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="a18ce-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a18ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="a18ce-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a18ce-106">[in]正在載入的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="a18ce-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a18ce-107">備註</span><span class="sxs-lookup"><span data-stu-id="a18ce-107">Remarks</span></span>  
 <span data-ttu-id="a18ce-108">值`moduleId`資訊要求之前無效[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="a18ce-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a18ce-109">需求</span><span class="sxs-lookup"><span data-stu-id="a18ce-109">Requirements</span></span>  
 <span data-ttu-id="a18ce-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a18ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a18ce-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a18ce-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a18ce-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a18ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a18ce-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a18ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18ce-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a18ce-114">See also</span></span>
- [<span data-ttu-id="a18ce-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a18ce-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
