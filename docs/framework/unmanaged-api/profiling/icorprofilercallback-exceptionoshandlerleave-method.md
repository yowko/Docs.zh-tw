---
title: ICorProfilerCallback::ExceptionOSHandlerLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: e54f87f5f02a1857fd9b7639d00d4bcb976665b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445413"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="6bd9d-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="6bd9d-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="6bd9d-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="6bd9d-103">Not implemented.</span></span> <span data-ttu-id="6bd9d-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span><span class="sxs-lookup"><span data-stu-id="6bd9d-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd9d-105">語法</span><span class="sxs-lookup"><span data-stu-id="6bd9d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6bd9d-106">需求</span><span class="sxs-lookup"><span data-stu-id="6bd9d-106">Requirements</span></span>  
 <span data-ttu-id="6bd9d-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd9d-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd9d-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6bd9d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6bd9d-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bd9d-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bd9d-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd9d-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd9d-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd9d-111">See also</span></span>

- [<span data-ttu-id="6bd9d-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6bd9d-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
