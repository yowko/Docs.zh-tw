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
ms.openlocfilehash: 47654d7ad1803e57f5db846ea0370d1f736deaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452269"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="4b406-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="4b406-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="4b406-103">通知記憶體回收控制代碼已建立的程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="4b406-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b406-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b406-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b406-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b406-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="4b406-106">[in]記憶體回收控制代碼的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b406-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="4b406-107">[in]記憶體回收控制代碼為其建立的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b406-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b406-108">需求</span><span class="sxs-lookup"><span data-stu-id="4b406-108">Requirements</span></span>  
 <span data-ttu-id="4b406-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b406-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b406-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b406-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b406-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b406-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b406-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b406-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b406-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b406-113">See Also</span></span>  
 [<span data-ttu-id="4b406-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4b406-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4b406-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="4b406-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
