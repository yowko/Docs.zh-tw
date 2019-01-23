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
ms.openlocfilehash: 7c8339142ef382ca029e9dd32c0270bd794ffcc2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546685"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="17b0f-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="17b0f-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="17b0f-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="17b0f-103">Not implemented.</span></span> <span data-ttu-id="17b0f-104">需要非受控例外狀況資訊的分析工具必須取得這項資訊透過其他方式。</span><span class="sxs-lookup"><span data-stu-id="17b0f-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b0f-105">語法</span><span class="sxs-lookup"><span data-stu-id="17b0f-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="17b0f-106">需求</span><span class="sxs-lookup"><span data-stu-id="17b0f-106">Requirements</span></span>  
 <span data-ttu-id="17b0f-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17b0f-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b0f-108">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17b0f-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17b0f-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17b0f-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17b0f-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b0f-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b0f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17b0f-111">See also</span></span>
- [<span data-ttu-id="17b0f-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="17b0f-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
