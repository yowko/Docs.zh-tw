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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d96f9853cfac8cef7b8af2e80b2e5d4196cdf79d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480217"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="fe945-102">ICorProfilerCallback::ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fe945-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="fe945-103">通知分析工具已完成載入的類別。</span><span class="sxs-lookup"><span data-stu-id="fe945-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe945-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe945-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe945-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe945-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="fe945-106">[in]識別已載入的類別。</span><span class="sxs-lookup"><span data-stu-id="fe945-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="fe945-107">[in]指出是否已成功載入類別的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="fe945-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe945-108">備註</span><span class="sxs-lookup"><span data-stu-id="fe945-108">Remarks</span></span>  
 <span data-ttu-id="fe945-109">值`classId`不是有效資訊要求直到`ClassLoadFinished`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="fe945-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="fe945-110">載入類別的某些部分可能會繼續之後`ClassLoadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="fe945-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="fe945-111">失敗 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="fe945-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fe945-112">不過，成功的 HRESULT 中`hrStatus`僅會指示已成功載入類別的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="fe945-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe945-113">需求</span><span class="sxs-lookup"><span data-stu-id="fe945-113">Requirements</span></span>  
 <span data-ttu-id="fe945-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe945-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe945-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe945-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe945-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe945-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe945-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe945-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe945-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe945-118">See also</span></span>
- [<span data-ttu-id="fe945-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fe945-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="fe945-120">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="fe945-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
