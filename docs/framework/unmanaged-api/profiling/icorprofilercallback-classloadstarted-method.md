---
title: "ICorProfilerCallback::ClassLoadStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f1622fdbbeb1f200f996e49c432600165a029aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="cb351-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="cb351-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="cb351-103">通知分析工具載入的類別。</span><span class="sxs-lookup"><span data-stu-id="cb351-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb351-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb351-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb351-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb351-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="cb351-106">[in]識別要載入的類別。</span><span class="sxs-lookup"><span data-stu-id="cb351-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb351-107">備註</span><span class="sxs-lookup"><span data-stu-id="cb351-107">Remarks</span></span>  
 <span data-ttu-id="cb351-108">值`classId`不正確的資訊要求，直到[icorprofilercallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="cb351-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb351-109">需求</span><span class="sxs-lookup"><span data-stu-id="cb351-109">Requirements</span></span>  
 <span data-ttu-id="cb351-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb351-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb351-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb351-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb351-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb351-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb351-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb351-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb351-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb351-114">See Also</span></span>  
 [<span data-ttu-id="cb351-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cb351-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
