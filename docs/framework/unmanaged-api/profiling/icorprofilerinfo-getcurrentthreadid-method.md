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
ms.openlocfilehash: 8be698d27ce69f955e5c1f17f5258602880c4021
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618694"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="7cfca-102">ICorProfilerInfo::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="7cfca-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="7cfca-103">如果它是受管理的執行緒，請取得目前執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7cfca-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cfca-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cfca-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cfca-105">參數</span><span class="sxs-lookup"><span data-stu-id="7cfca-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="7cfca-106">[out]傳回的識別碼，managed 執行緒的指標。</span><span class="sxs-lookup"><span data-stu-id="7cfca-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cfca-107">備註</span><span class="sxs-lookup"><span data-stu-id="7cfca-107">Remarks</span></span>  
 <span data-ttu-id="7cfca-108">如果目前的執行緒是內部的執行階段的執行緒或其他未受管理的執行緒`GetCurrentThreadID`HRESULT，以及傳回的值傳回 CORPROF_E_NOT_MANAGED_THREAD`pThreadId`參數是 null。</span><span class="sxs-lookup"><span data-stu-id="7cfca-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cfca-109">需求</span><span class="sxs-lookup"><span data-stu-id="7cfca-109">Requirements</span></span>  
 <span data-ttu-id="7cfca-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7cfca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cfca-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cfca-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cfca-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cfca-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cfca-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cfca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfca-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cfca-114">See also</span></span>
- [<span data-ttu-id="7cfca-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="7cfca-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
