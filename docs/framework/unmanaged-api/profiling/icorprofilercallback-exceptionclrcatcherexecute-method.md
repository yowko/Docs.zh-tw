---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b640a6dee9ae50278d6a844d20d21eae156e9dd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598542"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="3c55e-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="3c55e-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="3c55e-103">時呼叫`catch`封鎖例外狀況執行於 common language runtime (CLR) 本身內。</span><span class="sxs-lookup"><span data-stu-id="3c55e-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="3c55e-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="3c55e-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c55e-105">語法</span><span class="sxs-lookup"><span data-stu-id="3c55e-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3c55e-106">需求</span><span class="sxs-lookup"><span data-stu-id="3c55e-106">Requirements</span></span>  
 <span data-ttu-id="3c55e-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c55e-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c55e-108">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c55e-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c55e-109">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c55e-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c55e-110">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3c55e-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c55e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c55e-111">See also</span></span>

- [<span data-ttu-id="3c55e-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3c55e-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="3c55e-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="3c55e-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
