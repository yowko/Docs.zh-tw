---
title: "ICorProfilerInfo::GetThreadContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 630236e6f20b61d4a73bcb26a61112151a8ed80c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="75ab2-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="75ab2-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="75ab2-103">取得目前與指定的執行緒相關聯的內容識別。</span><span class="sxs-lookup"><span data-stu-id="75ab2-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ab2-104">語法</span><span class="sxs-lookup"><span data-stu-id="75ab2-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75ab2-105">參數</span><span class="sxs-lookup"><span data-stu-id="75ab2-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="75ab2-106">[in]執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="75ab2-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="75ab2-107">[out]目前與指定的執行緒相關聯的內容識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="75ab2-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="75ab2-108">如果執行緒沒有目前與它相關聯的內容，此函數會傳回 CORPROF_E_DATAINCOMPLETE。</span><span class="sxs-lookup"><span data-stu-id="75ab2-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ab2-109">需求</span><span class="sxs-lookup"><span data-stu-id="75ab2-109">Requirements</span></span>  
 <span data-ttu-id="75ab2-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75ab2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75ab2-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75ab2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75ab2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75ab2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75ab2-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75ab2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ab2-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="75ab2-114">See Also</span></span>  
 [<span data-ttu-id="75ab2-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="75ab2-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
