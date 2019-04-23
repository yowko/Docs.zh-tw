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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fcdd52e648b2461036921772b6b5684ba6aec22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175834"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="e7b49-102">ICorProfilerCallback::ExceptionOSHandlerEnter 方法</span><span class="sxs-lookup"><span data-stu-id="e7b49-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="e7b49-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="e7b49-103">Not implemented.</span></span> <span data-ttu-id="e7b49-104">需要非受控例外狀況資訊的分析工具必須取得這項資訊透過其他方式。</span><span class="sxs-lookup"><span data-stu-id="e7b49-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b49-105">語法</span><span class="sxs-lookup"><span data-stu-id="e7b49-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e7b49-106">需求</span><span class="sxs-lookup"><span data-stu-id="e7b49-106">Requirements</span></span>  
 <span data-ttu-id="e7b49-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7b49-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b49-108">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7b49-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7b49-109">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b49-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b49-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b49-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b49-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7b49-111">See also</span></span>

- [<span data-ttu-id="e7b49-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e7b49-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
