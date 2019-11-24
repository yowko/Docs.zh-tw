---
title: ICorProfilerInfo::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: bc4643f1c90b3ea4d3b561249a4e76ff304737bd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438770"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="74e8f-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="74e8f-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="74e8f-103">Gets the context identity currently associated with the specified thread.</span><span class="sxs-lookup"><span data-stu-id="74e8f-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="74e8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74e8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="74e8f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="74e8f-106">[in] The ID of the thread.</span><span class="sxs-lookup"><span data-stu-id="74e8f-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="74e8f-107">[out] A pointer to the context ID currently associated with the specified thread.</span><span class="sxs-lookup"><span data-stu-id="74e8f-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="74e8f-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="74e8f-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e8f-109">需求</span><span class="sxs-lookup"><span data-stu-id="74e8f-109">Requirements</span></span>  
 <span data-ttu-id="74e8f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74e8f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e8f-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74e8f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74e8f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74e8f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74e8f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e8f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e8f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="74e8f-114">See also</span></span>

- [<span data-ttu-id="74e8f-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="74e8f-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
