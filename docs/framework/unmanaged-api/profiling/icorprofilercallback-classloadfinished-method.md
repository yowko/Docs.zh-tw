---
title: ICorProfilerCallback::ClassLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 3be00d278a92398ad282a071f3e313e5de0e65a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700284"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="6e5b2-102">ICorProfilerCallback::ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="6e5b2-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>

<span data-ttu-id="6e5b2-103">通知分析工具某個類別已完成載入。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e5b2-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e5b2-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="6e5b2-106">\[in] 識別已載入的類別。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="6e5b2-107">\[in] 表示類別是否成功載入的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e5b2-108">備註</span><span class="sxs-lookup"><span data-stu-id="6e5b2-108">Remarks</span></span>  

 <span data-ttu-id="6e5b2-109">在呼叫方法之前，的值對 `classId` 資訊要求而言是不正確 `ClassLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="6e5b2-110">載入類別的某些部分可能會在回呼之後繼續進行 `ClassLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="6e5b2-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6e5b2-112">但是，中的成功 HRESULT `hrStatus` 只會指出載入類別的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e5b2-113">需求</span><span class="sxs-lookup"><span data-stu-id="6e5b2-113">Requirements</span></span>  

 <span data-ttu-id="6e5b2-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e5b2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5b2-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e5b2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e5b2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e5b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e5b2-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5b2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e5b2-118">See also</span></span>

- [<span data-ttu-id="6e5b2-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6e5b2-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6e5b2-120">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="6e5b2-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
