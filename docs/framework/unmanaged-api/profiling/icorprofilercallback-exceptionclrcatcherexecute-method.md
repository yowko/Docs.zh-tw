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
ms.openlocfilehash: f14dff33217656c35379a214f007ccb3642ef4b1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866451"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="08252-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="08252-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="08252-103">在 common language runtime （CLR）本身內執行例外狀況的 `catch` 區塊時呼叫。</span><span class="sxs-lookup"><span data-stu-id="08252-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="08252-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="08252-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08252-105">語法</span><span class="sxs-lookup"><span data-stu-id="08252-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="08252-106">需求</span><span class="sxs-lookup"><span data-stu-id="08252-106">Requirements</span></span>  
 <span data-ttu-id="08252-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08252-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08252-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08252-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08252-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08252-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08252-110">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="08252-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08252-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="08252-111">See also</span></span>

- [<span data-ttu-id="08252-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="08252-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="08252-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="08252-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
