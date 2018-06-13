---
title: ICorProfilerCallback::ExceptionSearchFilterLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13de3470e70635243aed78ac603cebc841c8fa59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451294"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="a363d-102">ICorProfilerCallback::ExceptionSearchFilterLeave 方法</span><span class="sxs-lookup"><span data-stu-id="a363d-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="a363d-103">通知分析工具，使用者篩選器剛剛完成執行。</span><span class="sxs-lookup"><span data-stu-id="a363d-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a363d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a363d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a363d-105">需求</span><span class="sxs-lookup"><span data-stu-id="a363d-105">Requirements</span></span>  
 <span data-ttu-id="a363d-106">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a363d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a363d-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a363d-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a363d-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a363d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a363d-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a363d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a363d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a363d-110">See Also</span></span>  
 [<span data-ttu-id="a363d-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a363d-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a363d-112">ExceptionSearchFilterEnter 方法</span><span class="sxs-lookup"><span data-stu-id="a363d-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
