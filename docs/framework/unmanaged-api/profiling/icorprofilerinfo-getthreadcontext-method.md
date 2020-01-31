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
ms.openlocfilehash: f8eff85392d355ea54980ac6b29e3c4cebb1b240
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869591"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="2b52f-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="2b52f-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="2b52f-103">取得目前與指定之執行緒相關聯的內容識別。</span><span class="sxs-lookup"><span data-stu-id="2b52f-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b52f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b52f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b52f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b52f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="2b52f-106">在執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b52f-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="2b52f-107">脫銷目前與指定的執行緒相關聯之內容識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="2b52f-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="2b52f-108">如果執行緒目前沒有相關聯的內容，此函數會傳回 CORPROF_E_DATAINCOMPLETE。</span><span class="sxs-lookup"><span data-stu-id="2b52f-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b52f-109">需求</span><span class="sxs-lookup"><span data-stu-id="2b52f-109">Requirements</span></span>  
 <span data-ttu-id="2b52f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b52f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b52f-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b52f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b52f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b52f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b52f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b52f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b52f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b52f-114">See also</span></span>

- [<span data-ttu-id="2b52f-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="2b52f-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
