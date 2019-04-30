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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f26fd93d42a709249936815d3c29ae572482f427
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992039"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="dbeac-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="dbeac-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="dbeac-103">取得目前與指定的執行緒相關聯的內容識別。</span><span class="sxs-lookup"><span data-stu-id="dbeac-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbeac-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbeac-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbeac-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbeac-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="dbeac-106">[in]執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="dbeac-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="dbeac-107">[out]目前與指定的執行緒相關聯的內容識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="dbeac-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="dbeac-108">如果執行緒沒有任何目前與它相關聯的內容，此函式會傳回 CORPROF_E_DATAINCOMPLETE。</span><span class="sxs-lookup"><span data-stu-id="dbeac-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbeac-109">需求</span><span class="sxs-lookup"><span data-stu-id="dbeac-109">Requirements</span></span>  
 <span data-ttu-id="dbeac-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbeac-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbeac-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dbeac-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dbeac-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbeac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbeac-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbeac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbeac-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbeac-114">See also</span></span>

- [<span data-ttu-id="dbeac-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="dbeac-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
