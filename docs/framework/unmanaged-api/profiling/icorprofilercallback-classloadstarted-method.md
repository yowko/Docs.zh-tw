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
ms.openlocfilehash: df70041497f000bfd4f6dcac2713e8d5e4eb33f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450940"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="9556a-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="9556a-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="9556a-103">通知分析工具載入的類別。</span><span class="sxs-lookup"><span data-stu-id="9556a-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9556a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9556a-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9556a-105">參數</span><span class="sxs-lookup"><span data-stu-id="9556a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9556a-106">[in]識別要載入的類別。</span><span class="sxs-lookup"><span data-stu-id="9556a-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9556a-107">備註</span><span class="sxs-lookup"><span data-stu-id="9556a-107">Remarks</span></span>  
 <span data-ttu-id="9556a-108">值`classId`不正確的資訊要求，直到[icorprofilercallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="9556a-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9556a-109">需求</span><span class="sxs-lookup"><span data-stu-id="9556a-109">Requirements</span></span>  
 <span data-ttu-id="9556a-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9556a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9556a-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9556a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9556a-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9556a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9556a-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9556a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9556a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9556a-114">See Also</span></span>  
 [<span data-ttu-id="9556a-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9556a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
