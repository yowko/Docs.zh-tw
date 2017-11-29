---
title: "ICorProfilerInfo::GetThreadContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetThreadContext
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f2802c89a72b6c6c9e268d9d35767ca5b6dadce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="1d981-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="1d981-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="1d981-103">取得目前與指定的執行緒相關聯的內容識別。</span><span class="sxs-lookup"><span data-stu-id="1d981-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d981-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d981-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d981-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d981-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1d981-106">[in]執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d981-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="1d981-107">[out]目前與指定的執行緒相關聯的內容識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="1d981-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="1d981-108">如果執行緒沒有目前與它相關聯的內容，此函數會傳回 CORPROF_E_DATAINCOMPLETE。</span><span class="sxs-lookup"><span data-stu-id="1d981-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d981-109">需求</span><span class="sxs-lookup"><span data-stu-id="1d981-109">Requirements</span></span>  
 <span data-ttu-id="1d981-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d981-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d981-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d981-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d981-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d981-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d981-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d981-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d981-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d981-114">See Also</span></span>  
 [<span data-ttu-id="1d981-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1d981-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
