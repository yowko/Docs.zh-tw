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
ms.openlocfilehash: 1a9e377ba98c0c2302e341149bd5acb46c24051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699985"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="70a02-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="70a02-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>

<span data-ttu-id="70a02-103">當例外狀況的 `catch` 區塊在 common language runtime (CLR) 本身執行時呼叫。</span><span class="sxs-lookup"><span data-stu-id="70a02-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="70a02-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="70a02-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a02-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="70a02-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="70a02-106">需求</span><span class="sxs-lookup"><span data-stu-id="70a02-106">Requirements</span></span>  

 <span data-ttu-id="70a02-107">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70a02-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a02-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70a02-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70a02-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70a02-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70a02-110">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="70a02-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a02-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70a02-111">See also</span></span>

- [<span data-ttu-id="70a02-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="70a02-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="70a02-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="70a02-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
