---
title: ICorProfilerCallback2::HandleCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d5ea547066663564d76008434884b6e34150efb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779333"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="fd579-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="fd579-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="fd579-103">通知程式碼分析工具已建立的記憶體回收控制代碼。</span><span class="sxs-lookup"><span data-stu-id="fd579-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd579-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd579-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd579-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd579-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="fd579-106">[in]進行記憶體回收控制代碼的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd579-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="fd579-107">[in]為其建立記憶體回收控制代碼的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd579-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd579-108">需求</span><span class="sxs-lookup"><span data-stu-id="fd579-108">Requirements</span></span>  
 <span data-ttu-id="fd579-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd579-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd579-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd579-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd579-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd579-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd579-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd579-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd579-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd579-113">See also</span></span>

- [<span data-ttu-id="fd579-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fd579-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="fd579-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="fd579-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
