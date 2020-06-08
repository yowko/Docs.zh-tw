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
ms.openlocfilehash: b79c8dd9f27805e00535dde53c6ee9f5ee457b42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500259"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="84808-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="84808-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="84808-103">當例外狀況的 `catch` 區塊在 common language runtime （CLR）本身內執行時呼叫。</span><span class="sxs-lookup"><span data-stu-id="84808-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="84808-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="84808-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84808-105">語法</span><span class="sxs-lookup"><span data-stu-id="84808-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="84808-106">規格需求</span><span class="sxs-lookup"><span data-stu-id="84808-106">Requirements</span></span>  
 <span data-ttu-id="84808-107">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84808-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84808-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84808-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84808-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84808-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84808-110">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="84808-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84808-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84808-111">See also</span></span>

- [<span data-ttu-id="84808-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="84808-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="84808-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="84808-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
