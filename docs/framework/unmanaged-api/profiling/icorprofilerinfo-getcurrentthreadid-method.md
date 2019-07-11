---
title: ICorProfilerInfo::GetCurrentThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db5ed871734205d59c602cc8b5c0cc9e8ac4682a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762867"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="92cc9-102">ICorProfilerInfo::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="92cc9-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="92cc9-103">如果它是受管理的執行緒，請取得目前執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="92cc9-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92cc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="92cc9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92cc9-105">參數</span><span class="sxs-lookup"><span data-stu-id="92cc9-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="92cc9-106">[out]傳回的識別碼，managed 執行緒的指標。</span><span class="sxs-lookup"><span data-stu-id="92cc9-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92cc9-107">備註</span><span class="sxs-lookup"><span data-stu-id="92cc9-107">Remarks</span></span>  
 <span data-ttu-id="92cc9-108">如果目前的執行緒是內部的執行階段的執行緒或其他未受管理的執行緒`GetCurrentThreadID`HRESULT，以及傳回的值傳回 CORPROF_E_NOT_MANAGED_THREAD`pThreadId`參數是 null。</span><span class="sxs-lookup"><span data-stu-id="92cc9-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92cc9-109">需求</span><span class="sxs-lookup"><span data-stu-id="92cc9-109">Requirements</span></span>  
 <span data-ttu-id="92cc9-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92cc9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92cc9-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92cc9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92cc9-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92cc9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92cc9-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92cc9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cc9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92cc9-114">See also</span></span>

- [<span data-ttu-id="92cc9-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="92cc9-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
