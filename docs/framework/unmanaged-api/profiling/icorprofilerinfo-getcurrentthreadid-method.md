---
title: "ICorProfilerInfo::GetCurrentThreadID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCurrentThreadID
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 055a5f56f076cc29ca7ce5d45ecedd650e8f2f44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="8351b-102">ICorProfilerInfo::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="8351b-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="8351b-103">取得目前執行緒的識別碼，如果有 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8351b-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8351b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8351b-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8351b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8351b-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="8351b-106">[out]傳回 managed 執行緒的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="8351b-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8351b-107">備註</span><span class="sxs-lookup"><span data-stu-id="8351b-107">Remarks</span></span>  
 <span data-ttu-id="8351b-108">如果目前的執行緒是內部執行階段執行緒或其他未受管理的執行緒， `GetCurrentThreadID` CORPROF_E_NOT_MANAGED_THREAD 傳回 HRESULT，以及傳回的值的`pThreadId`參數是 null。</span><span class="sxs-lookup"><span data-stu-id="8351b-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8351b-109">需求</span><span class="sxs-lookup"><span data-stu-id="8351b-109">Requirements</span></span>  
 <span data-ttu-id="8351b-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8351b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8351b-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8351b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8351b-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8351b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8351b-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8351b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8351b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8351b-114">See Also</span></span>  
 [<span data-ttu-id="8351b-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8351b-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
