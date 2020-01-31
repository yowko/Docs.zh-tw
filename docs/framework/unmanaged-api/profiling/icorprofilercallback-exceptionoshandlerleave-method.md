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
ms.openlocfilehash: dcb2af2507306b22da14c13a42e4019261c8fa8c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866438"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="3e38b-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="3e38b-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="3e38b-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="3e38b-103">Not implemented.</span></span> <span data-ttu-id="3e38b-104">需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。</span><span class="sxs-lookup"><span data-stu-id="3e38b-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e38b-105">語法</span><span class="sxs-lookup"><span data-stu-id="3e38b-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3e38b-106">需求</span><span class="sxs-lookup"><span data-stu-id="3e38b-106">Requirements</span></span>  
 <span data-ttu-id="3e38b-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e38b-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e38b-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3e38b-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e38b-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e38b-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e38b-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e38b-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e38b-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e38b-111">See also</span></span>

- [<span data-ttu-id="3e38b-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3e38b-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
