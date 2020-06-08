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
ms.openlocfilehash: c2c9ed848984d36ddf10d32d120deda76a4d47cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500282"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="a2144-102">ICorProfilerCallback::ExceptionOSHandlerEnter 方法</span><span class="sxs-lookup"><span data-stu-id="a2144-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="a2144-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="a2144-103">Not implemented.</span></span> <span data-ttu-id="a2144-104">需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。</span><span class="sxs-lookup"><span data-stu-id="a2144-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2144-105">語法</span><span class="sxs-lookup"><span data-stu-id="a2144-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a2144-106">規格需求</span><span class="sxs-lookup"><span data-stu-id="a2144-106">Requirements</span></span>  
 <span data-ttu-id="a2144-107">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2144-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2144-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2144-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2144-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2144-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2144-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2144-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2144-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2144-111">See also</span></span>

- [<span data-ttu-id="a2144-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a2144-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
