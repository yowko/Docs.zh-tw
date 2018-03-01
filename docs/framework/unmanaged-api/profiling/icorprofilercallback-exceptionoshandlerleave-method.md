---
title: "ICorProfilerCallback::ExceptionOSHandlerLeave 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b42902ceb6210d1189f600f61ef703d9b2029893
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="b0e98-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="b0e98-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="b0e98-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="b0e98-103">Not implemented.</span></span> <span data-ttu-id="b0e98-104">分析工具所需的 unmanaged 例外狀況資訊必須取得這項資訊透過其他方式。</span><span class="sxs-lookup"><span data-stu-id="b0e98-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e98-105">語法</span><span class="sxs-lookup"><span data-stu-id="b0e98-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b0e98-106">需求</span><span class="sxs-lookup"><span data-stu-id="b0e98-106">Requirements</span></span>  
 <span data-ttu-id="b0e98-107">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e98-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e98-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0e98-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0e98-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0e98-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0e98-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e98-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e98-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e98-111">See Also</span></span>  
 [<span data-ttu-id="b0e98-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b0e98-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
