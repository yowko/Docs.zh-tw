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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53c71914d8938067ceb5d580d42ffe7d7d8dc1df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450661"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="98c91-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="98c91-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="98c91-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="98c91-103">Not implemented.</span></span> <span data-ttu-id="98c91-104">分析工具所需的 unmanaged 例外狀況資訊必須取得這項資訊透過其他方式。</span><span class="sxs-lookup"><span data-stu-id="98c91-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c91-105">語法</span><span class="sxs-lookup"><span data-stu-id="98c91-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="98c91-106">需求</span><span class="sxs-lookup"><span data-stu-id="98c91-106">Requirements</span></span>  
 <span data-ttu-id="98c91-107">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98c91-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c91-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98c91-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98c91-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98c91-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98c91-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c91-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c91-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98c91-111">See Also</span></span>  
 [<span data-ttu-id="98c91-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="98c91-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
