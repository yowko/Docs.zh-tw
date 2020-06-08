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
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503350"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="4a205-102">ICorProfilerCallback::ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="4a205-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="4a205-103">通知分析工具已載入模組。</span><span class="sxs-lookup"><span data-stu-id="4a205-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a205-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a205-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a205-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a205-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4a205-106">在正在載入之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a205-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a205-107">備註</span><span class="sxs-lookup"><span data-stu-id="4a205-107">Remarks</span></span>  
 <span data-ttu-id="4a205-108">在 `moduleId` 呼叫[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)方法之前，的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="4a205-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a205-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="4a205-109">Requirements</span></span>  
 <span data-ttu-id="4a205-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a205-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a205-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a205-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a205-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a205-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a205-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a205-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a205-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a205-114">See also</span></span>

- [<span data-ttu-id="4a205-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4a205-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
