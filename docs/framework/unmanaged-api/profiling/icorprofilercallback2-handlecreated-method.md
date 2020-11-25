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
ms.openlocfilehash: 6cd931f6c680a07327915ab4680702af298ca1ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717304"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="85f13-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="85f13-102">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="85f13-103">通知程式碼分析工具已建立垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="85f13-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f13-104">語法</span><span class="sxs-lookup"><span data-stu-id="85f13-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85f13-105">參數</span><span class="sxs-lookup"><span data-stu-id="85f13-105">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="85f13-106">在垃圾收集之控制碼的識別碼。</span><span class="sxs-lookup"><span data-stu-id="85f13-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="85f13-107">在建立垃圾收集控制碼之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="85f13-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f13-108">需求</span><span class="sxs-lookup"><span data-stu-id="85f13-108">Requirements</span></span>  

 <span data-ttu-id="85f13-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85f13-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f13-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85f13-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85f13-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85f13-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85f13-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f13-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f13-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85f13-113">See also</span></span>

- [<span data-ttu-id="85f13-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="85f13-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="85f13-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="85f13-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
