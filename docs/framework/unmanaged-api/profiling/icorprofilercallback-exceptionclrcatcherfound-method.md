---
title: ICorProfilerCallback::ExceptionCLRCatcherFound 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59225677671388b4ed31f7fa440b6e502b604c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073010"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="bc24c-102">ICorProfilerCallback::ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="bc24c-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="bc24c-103">時呼叫`catch`封鎖 common language runtime (CLR) 本身內發現例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bc24c-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="bc24c-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="bc24c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc24c-105">語法</span><span class="sxs-lookup"><span data-stu-id="bc24c-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="bc24c-106">需求</span><span class="sxs-lookup"><span data-stu-id="bc24c-106">Requirements</span></span>  
 <span data-ttu-id="bc24c-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc24c-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc24c-108">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bc24c-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc24c-109">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc24c-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc24c-110">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="bc24c-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc24c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc24c-111">See also</span></span>

- [<span data-ttu-id="bc24c-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bc24c-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bc24c-113">ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="bc24c-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
