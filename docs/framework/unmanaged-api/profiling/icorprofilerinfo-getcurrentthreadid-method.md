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
ms.openlocfilehash: fc5356f097f869403212cd234a508f1f29c5ec94
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450381"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="41129-102">ICorProfilerInfo::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="41129-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="41129-103">取得目前線程的識別碼（如果它是 managed 執行緒）。</span><span class="sxs-lookup"><span data-stu-id="41129-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41129-104">語法</span><span class="sxs-lookup"><span data-stu-id="41129-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41129-105">參數</span><span class="sxs-lookup"><span data-stu-id="41129-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="41129-106">脫銷Managed 執行緒之傳回識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="41129-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41129-107">備註</span><span class="sxs-lookup"><span data-stu-id="41129-107">Remarks</span></span>  
 <span data-ttu-id="41129-108">如果目前的執行緒是內部運行時間表程或其他非受控執行緒，`GetCurrentThreadID` 會傳回 CORPROF_E_NOT_MANAGED_THREAD 做為 HRESULT，而 `pThreadId` 參數的傳回值將會是 null。</span><span class="sxs-lookup"><span data-stu-id="41129-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41129-109">需求</span><span class="sxs-lookup"><span data-stu-id="41129-109">Requirements</span></span>  
 <span data-ttu-id="41129-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41129-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41129-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41129-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41129-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41129-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41129-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41129-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41129-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41129-114">See also</span></span>

- [<span data-ttu-id="41129-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="41129-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
