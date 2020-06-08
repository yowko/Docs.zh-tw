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
ms.openlocfilehash: 772f0c00bb850e35a6f5bf7fa4df2b3052999df5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499788"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="d4700-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="d4700-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="d4700-103">通知程式碼分析工具，已建立垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="d4700-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4700-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4700-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4700-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4700-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="d4700-106">在垃圾收集的控制碼識別碼。</span><span class="sxs-lookup"><span data-stu-id="d4700-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="d4700-107">在已建立垃圾收集控制碼之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d4700-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4700-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="d4700-108">Requirements</span></span>  
 <span data-ttu-id="d4700-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4700-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4700-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4700-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4700-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4700-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4700-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4700-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4700-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4700-113">See also</span></span>

- [<span data-ttu-id="d4700-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d4700-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d4700-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="d4700-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
