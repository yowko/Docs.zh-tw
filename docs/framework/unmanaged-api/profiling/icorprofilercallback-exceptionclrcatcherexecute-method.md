---
title: "ICorProfilerCallback::ExceptionCLRCatcherExecute 方法"
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
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5d278fa196836d18b8515bee5af1946b2ca4d74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="abde6-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="abde6-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="abde6-103">時呼叫`catch`封鎖在 common language runtime (CLR) 本身內執行例外狀況。</span><span class="sxs-lookup"><span data-stu-id="abde6-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="abde6-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="abde6-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abde6-105">語法</span><span class="sxs-lookup"><span data-stu-id="abde6-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="abde6-106">需求</span><span class="sxs-lookup"><span data-stu-id="abde6-106">Requirements</span></span>  
 <span data-ttu-id="abde6-107">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abde6-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abde6-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abde6-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abde6-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abde6-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abde6-110">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="abde6-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abde6-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="abde6-111">See Also</span></span>  
 [<span data-ttu-id="abde6-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="abde6-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="abde6-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="abde6-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
