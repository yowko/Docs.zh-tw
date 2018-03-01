---
title: "ICorProfilerCallback::ExceptionOSHandlerEnter 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c26260a2f70537deefb5600c0b721e0c0faf0399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="f2aae-102">ICorProfilerCallback::ExceptionOSHandlerEnter 方法</span><span class="sxs-lookup"><span data-stu-id="f2aae-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="f2aae-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="f2aae-103">Not implemented.</span></span> <span data-ttu-id="f2aae-104">分析工具所需的 unmanaged 例外狀況資訊必須取得這項資訊透過其他方式。</span><span class="sxs-lookup"><span data-stu-id="f2aae-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2aae-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2aae-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f2aae-106">需求</span><span class="sxs-lookup"><span data-stu-id="f2aae-106">Requirements</span></span>  
 <span data-ttu-id="f2aae-107">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2aae-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2aae-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2aae-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2aae-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2aae-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2aae-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2aae-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2aae-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2aae-111">See Also</span></span>  
 [<span data-ttu-id="f2aae-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f2aae-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
