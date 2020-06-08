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
ms.openlocfilehash: 4f4d53b086453adce38902518f2de3dde1f2812f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500243"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="a7f41-102">ICorProfilerCallback::ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="a7f41-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="a7f41-103">在 `catch` common language runtime （CLR）本身內找到例外狀況的區塊時呼叫。</span><span class="sxs-lookup"><span data-stu-id="a7f41-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="a7f41-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="a7f41-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f41-105">語法</span><span class="sxs-lookup"><span data-stu-id="a7f41-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a7f41-106">規格需求</span><span class="sxs-lookup"><span data-stu-id="a7f41-106">Requirements</span></span>  
 <span data-ttu-id="a7f41-107">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7f41-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f41-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a7f41-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7f41-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7f41-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7f41-110">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="a7f41-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f41-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7f41-111">See also</span></span>

- [<span data-ttu-id="a7f41-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a7f41-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a7f41-113">ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="a7f41-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
