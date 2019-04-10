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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224620"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="e1bc0-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="e1bc0-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="e1bc0-103">取得目前與指定的執行緒相關聯的內容識別。</span><span class="sxs-lookup"><span data-stu-id="e1bc0-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1bc0-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1bc0-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1bc0-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e1bc0-106">[in]執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="e1bc0-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="e1bc0-107">[out]目前與指定的執行緒相關聯的內容識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="e1bc0-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="e1bc0-108">如果執行緒沒有任何目前與它相關聯的內容，此函式會傳回 CORPROF_E_DATAINCOMPLETE。</span><span class="sxs-lookup"><span data-stu-id="e1bc0-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1bc0-109">需求</span><span class="sxs-lookup"><span data-stu-id="e1bc0-109">Requirements</span></span>  
 <span data-ttu-id="e1bc0-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1bc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1bc0-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1bc0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1bc0-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1bc0-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e1bc0-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e1bc0-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1bc0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1bc0-114">See also</span></span>

- [<span data-ttu-id="e1bc0-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e1bc0-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
