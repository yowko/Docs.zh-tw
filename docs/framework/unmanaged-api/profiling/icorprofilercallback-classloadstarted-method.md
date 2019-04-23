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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db7a033944272756a739dec39d4df11fde1d48b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178603"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="263ca-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="263ca-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="263ca-103">通知分析工具載入的類別。</span><span class="sxs-lookup"><span data-stu-id="263ca-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="263ca-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="263ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="263ca-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="263ca-106">[in]識別要載入的類別。</span><span class="sxs-lookup"><span data-stu-id="263ca-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="263ca-107">備註</span><span class="sxs-lookup"><span data-stu-id="263ca-107">Remarks</span></span>  
 <span data-ttu-id="263ca-108">值`classId`資訊要求之前無效[icorprofilercallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="263ca-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263ca-109">需求</span><span class="sxs-lookup"><span data-stu-id="263ca-109">Requirements</span></span>  
 <span data-ttu-id="263ca-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="263ca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263ca-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="263ca-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="263ca-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="263ca-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="263ca-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263ca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263ca-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="263ca-114">See also</span></span>

- [<span data-ttu-id="263ca-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="263ca-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
