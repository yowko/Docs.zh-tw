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
ms.openlocfilehash: 6fbd009b5785c5dc78df81e4411fbdf8e8eadf71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730327"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="85625-102">ICorProfilerCallback::ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="85625-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>

<span data-ttu-id="85625-103">通知 profiler 正在載入模組。</span><span class="sxs-lookup"><span data-stu-id="85625-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85625-104">語法</span><span class="sxs-lookup"><span data-stu-id="85625-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85625-105">參數</span><span class="sxs-lookup"><span data-stu-id="85625-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="85625-106">在正在載入之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="85625-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85625-107">備註</span><span class="sxs-lookup"><span data-stu-id="85625-107">Remarks</span></span>  

 <span data-ttu-id="85625-108">在 `moduleId` 呼叫 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 方法之前，的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="85625-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85625-109">需求</span><span class="sxs-lookup"><span data-stu-id="85625-109">Requirements</span></span>  

 <span data-ttu-id="85625-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85625-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85625-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85625-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85625-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85625-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85625-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85625-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85625-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85625-114">See also</span></span>

- [<span data-ttu-id="85625-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="85625-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
