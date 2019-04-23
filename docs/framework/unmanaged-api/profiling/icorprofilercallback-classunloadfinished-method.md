---
title: ICorProfilerCallback::ClassUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d01f3d7485b19c076d9cd3e83aeccbcf5e728f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160702"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="e40d7-102">ICorProfilerCallback::ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="e40d7-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="e40d7-103">通知分析工具已完成卸載類別。</span><span class="sxs-lookup"><span data-stu-id="e40d7-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e40d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e40d7-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e40d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e40d7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e40d7-106">[in]識別已卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="e40d7-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="e40d7-107">[in]HRESULT，指出類別是否卸載成功。</span><span class="sxs-lookup"><span data-stu-id="e40d7-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e40d7-108">備註</span><span class="sxs-lookup"><span data-stu-id="e40d7-108">Remarks</span></span>  
 <span data-ttu-id="e40d7-109">卸載類別的某些部分可能會繼續之後`ClassUnloadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="e40d7-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="e40d7-110">失敗 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="e40d7-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e40d7-111">不過，成功的 HRESULT 中`hrStatus`僅會指示已成功卸載類別的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="e40d7-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e40d7-112">需求</span><span class="sxs-lookup"><span data-stu-id="e40d7-112">Requirements</span></span>  
 <span data-ttu-id="e40d7-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e40d7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e40d7-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e40d7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e40d7-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e40d7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e40d7-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e40d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40d7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e40d7-117">See also</span></span>

- [<span data-ttu-id="e40d7-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e40d7-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e40d7-119">ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="e40d7-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
