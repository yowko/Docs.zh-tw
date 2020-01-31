---
title: ICorProfilerCallback::ExceptionOSHandlerEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
ms.openlocfilehash: e27fd3147182e8c820fb1d30f172e0517ca4e77e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866468"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="d8af8-102">ICorProfilerCallback::ExceptionOSHandlerEnter 方法</span><span class="sxs-lookup"><span data-stu-id="d8af8-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="d8af8-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="d8af8-103">Not implemented.</span></span> <span data-ttu-id="d8af8-104">需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。</span><span class="sxs-lookup"><span data-stu-id="d8af8-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8af8-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8af8-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d8af8-106">需求</span><span class="sxs-lookup"><span data-stu-id="d8af8-106">Requirements</span></span>  
 <span data-ttu-id="d8af8-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8af8-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8af8-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8af8-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8af8-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8af8-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8af8-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8af8-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8af8-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8af8-111">See also</span></span>

- [<span data-ttu-id="d8af8-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d8af8-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
