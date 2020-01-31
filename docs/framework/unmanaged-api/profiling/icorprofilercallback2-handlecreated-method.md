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
ms.openlocfilehash: 0c25a5cad01ef0eb268e90c38bd24d638b6f8cc4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865762"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="0008b-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="0008b-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="0008b-103">通知程式碼分析工具，已建立垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="0008b-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0008b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0008b-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0008b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0008b-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="0008b-106">在垃圾收集的控制碼識別碼。</span><span class="sxs-lookup"><span data-stu-id="0008b-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="0008b-107">在已建立垃圾收集控制碼之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0008b-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0008b-108">需求</span><span class="sxs-lookup"><span data-stu-id="0008b-108">Requirements</span></span>  
 <span data-ttu-id="0008b-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0008b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0008b-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0008b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0008b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0008b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0008b-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0008b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0008b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="0008b-113">See also</span></span>

- [<span data-ttu-id="0008b-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0008b-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0008b-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="0008b-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
