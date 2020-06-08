---
title: ICorProfilerCallback::ClassLoadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500360"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="31410-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="31410-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="31410-103">通知分析工具，正在載入類別。</span><span class="sxs-lookup"><span data-stu-id="31410-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31410-104">語法</span><span class="sxs-lookup"><span data-stu-id="31410-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31410-105">參數</span><span class="sxs-lookup"><span data-stu-id="31410-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="31410-106">\[在中，識別要載入的類別。</span><span class="sxs-lookup"><span data-stu-id="31410-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="31410-107">備註</span><span class="sxs-lookup"><span data-stu-id="31410-107">Remarks</span></span>  
 <span data-ttu-id="31410-108">在 `classId` 呼叫[ICorProfilerCallback：： ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)方法之前，的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="31410-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31410-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="31410-109">Requirements</span></span>  
 <span data-ttu-id="31410-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31410-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31410-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31410-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31410-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31410-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31410-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31410-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31410-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31410-114">See also</span></span>

- [<span data-ttu-id="31410-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="31410-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
