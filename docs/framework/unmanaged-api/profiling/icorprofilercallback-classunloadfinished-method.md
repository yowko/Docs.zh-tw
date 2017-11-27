---
title: "ICorProfilerCallback::ClassUnloadFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 920fa36edcc49c12f8f73644cc4e6551a0e954ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="10540-102">ICorProfilerCallback::ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="10540-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="10540-103">通知分析工具已完成卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="10540-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10540-104">語法</span><span class="sxs-lookup"><span data-stu-id="10540-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10540-105">參數</span><span class="sxs-lookup"><span data-stu-id="10540-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="10540-106">[in]識別已卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="10540-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="10540-107">[in]HRESULT，指出類別是否卸載成功。</span><span class="sxs-lookup"><span data-stu-id="10540-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10540-108">備註</span><span class="sxs-lookup"><span data-stu-id="10540-108">Remarks</span></span>  
 <span data-ttu-id="10540-109">卸載的類別的某些部分可能會繼續之後`ClassUnloadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="10540-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="10540-110">失敗的 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="10540-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="10540-111">不過，成功 HRESULT 中`hrStatus`只會指出已成功卸載類別的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="10540-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10540-112">需求</span><span class="sxs-lookup"><span data-stu-id="10540-112">Requirements</span></span>  
 <span data-ttu-id="10540-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10540-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10540-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10540-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10540-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10540-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10540-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10540-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10540-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10540-117">See Also</span></span>  
 [<span data-ttu-id="10540-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="10540-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="10540-119">ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="10540-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
