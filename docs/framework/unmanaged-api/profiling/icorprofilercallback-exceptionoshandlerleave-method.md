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
ms.openlocfilehash: 37e3c9139a202e3cb31bd824d182389ae10b7389
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699920"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="2f7eb-102">ICorProfilerCallback::ExceptionOSHandlerLeave 方法</span><span class="sxs-lookup"><span data-stu-id="2f7eb-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="2f7eb-103">未實作。</span><span class="sxs-lookup"><span data-stu-id="2f7eb-103">Not implemented.</span></span> <span data-ttu-id="2f7eb-104">需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。</span><span class="sxs-lookup"><span data-stu-id="2f7eb-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7eb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f7eb-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2f7eb-106">需求</span><span class="sxs-lookup"><span data-stu-id="2f7eb-106">Requirements</span></span>  

 <span data-ttu-id="2f7eb-107">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f7eb-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f7eb-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f7eb-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f7eb-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f7eb-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f7eb-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f7eb-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7eb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f7eb-111">See also</span></span>

- [<span data-ttu-id="2f7eb-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2f7eb-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
