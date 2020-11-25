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
ms.openlocfilehash: 273c3cefa2e67a7d8c429982b4da4126168b2830
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699959"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="e87cd-102">ICorProfilerCallback::ExceptionOSHandlerEnter 方法</span><span class="sxs-lookup"><span data-stu-id="e87cd-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>

<span data-ttu-id="e87cd-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="e87cd-103">Not implemented.</span></span> <span data-ttu-id="e87cd-104">需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。</span><span class="sxs-lookup"><span data-stu-id="e87cd-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e87cd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e87cd-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e87cd-106">需求</span><span class="sxs-lookup"><span data-stu-id="e87cd-106">Requirements</span></span>  

 <span data-ttu-id="e87cd-107">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e87cd-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e87cd-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e87cd-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e87cd-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e87cd-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e87cd-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e87cd-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87cd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e87cd-111">See also</span></span>

- [<span data-ttu-id="e87cd-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e87cd-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
