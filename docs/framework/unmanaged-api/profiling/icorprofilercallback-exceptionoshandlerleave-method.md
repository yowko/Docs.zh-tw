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
ms.openlocfilehash: 468c5b28bb5a574aacf623196f0c516992473707
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756234"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="1d550-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="1d550-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="1d550-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="1d550-103">Not implemented.</span></span> <span data-ttu-id="1d550-104">需要非受控例外狀況資訊的分析工具必須取得這項資訊透過其他方式。</span><span class="sxs-lookup"><span data-stu-id="1d550-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d550-105">語法</span><span class="sxs-lookup"><span data-stu-id="1d550-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1d550-106">需求</span><span class="sxs-lookup"><span data-stu-id="1d550-106">Requirements</span></span>  
 <span data-ttu-id="1d550-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d550-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d550-108">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d550-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d550-109">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d550-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d550-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d550-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d550-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d550-111">See also</span></span>

- [<span data-ttu-id="1d550-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1d550-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
