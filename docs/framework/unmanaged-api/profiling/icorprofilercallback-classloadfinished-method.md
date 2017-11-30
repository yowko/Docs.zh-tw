---
title: "ICorProfilerCallback::ClassLoadFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3f321849c62ffd653ffa174ff91447a2c8eec73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="096e4-102">ICorProfilerCallback::ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="096e4-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="096e4-103">通知分析工具已完成載入類別。</span><span class="sxs-lookup"><span data-stu-id="096e4-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="096e4-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="096e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="096e4-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="096e4-106">[in]識別已載入的類別。</span><span class="sxs-lookup"><span data-stu-id="096e4-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="096e4-107">[in]HRESULT，指出是否已成功載入類別。</span><span class="sxs-lookup"><span data-stu-id="096e4-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="096e4-108">備註</span><span class="sxs-lookup"><span data-stu-id="096e4-108">Remarks</span></span>  
 <span data-ttu-id="096e4-109">值`classId`不正確的資訊要求，直到`ClassLoadFinished`方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="096e4-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="096e4-110">載入類別的某些部分可能會繼續之後`ClassLoadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="096e4-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="096e4-111">失敗的 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="096e4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="096e4-112">不過，成功 HRESULT 中`hrStatus`只會指出已成功載入類別的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="096e4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096e4-113">需求</span><span class="sxs-lookup"><span data-stu-id="096e4-113">Requirements</span></span>  
 <span data-ttu-id="096e4-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="096e4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096e4-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="096e4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="096e4-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="096e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="096e4-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096e4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="096e4-118">See Also</span></span>  
 [<span data-ttu-id="096e4-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="096e4-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="096e4-120">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="096e4-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
