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
ms.openlocfilehash: fd80c598401d7c72b1b67445b474470ae14736cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501905"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="f8d9c-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="f8d9c-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="f8d9c-103">通知程式碼分析工具已建立的記憶體回收控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f8d9c-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8d9c-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8d9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8d9c-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="f8d9c-106">[in]進行記憶體回收控制代碼的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f8d9c-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="f8d9c-107">[in]為其建立記憶體回收控制代碼的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="f8d9c-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8d9c-108">需求</span><span class="sxs-lookup"><span data-stu-id="f8d9c-108">Requirements</span></span>  
 <span data-ttu-id="f8d9c-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8d9c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d9c-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8d9c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8d9c-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8d9c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8d9c-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d9c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d9c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d9c-113">See also</span></span>
- [<span data-ttu-id="f8d9c-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f8d9c-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f8d9c-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="f8d9c-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
