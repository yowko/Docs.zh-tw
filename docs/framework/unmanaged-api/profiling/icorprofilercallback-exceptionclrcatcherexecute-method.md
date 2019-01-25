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
ms.openlocfilehash: e92ca55a04032ad9950888eb59e33ee815b14d42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514600"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="f7efc-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="f7efc-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="f7efc-103">時呼叫`catch`封鎖例外狀況執行於 common language runtime (CLR) 本身內。</span><span class="sxs-lookup"><span data-stu-id="f7efc-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="f7efc-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="f7efc-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7efc-105">語法</span><span class="sxs-lookup"><span data-stu-id="f7efc-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f7efc-106">需求</span><span class="sxs-lookup"><span data-stu-id="f7efc-106">Requirements</span></span>  
 <span data-ttu-id="f7efc-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7efc-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7efc-108">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7efc-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7efc-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7efc-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7efc-110">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f7efc-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7efc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7efc-111">See also</span></span>
- [<span data-ttu-id="f7efc-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f7efc-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f7efc-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="f7efc-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
