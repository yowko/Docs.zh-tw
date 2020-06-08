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
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498397"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="8d48a-102">ICorProfilerInfo::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="8d48a-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="8d48a-103">取得目前線程的識別碼（如果它是 managed 執行緒）。</span><span class="sxs-lookup"><span data-stu-id="8d48a-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d48a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d48a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d48a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d48a-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="8d48a-106">脫銷Managed 執行緒之傳回識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="8d48a-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d48a-107">備註</span><span class="sxs-lookup"><span data-stu-id="8d48a-107">Remarks</span></span>  
 <span data-ttu-id="8d48a-108">如果目前的執行緒是內部運行時間表程或其他非受控執行緒，則 `GetCurrentThreadID` 會傳回 CORPROF_E_NOT_MANAGED_THREAD 做為 HRESULT，而參數的傳回值 `pThreadId` 將會是 null。</span><span class="sxs-lookup"><span data-stu-id="8d48a-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d48a-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="8d48a-109">Requirements</span></span>  
 <span data-ttu-id="8d48a-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d48a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d48a-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d48a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d48a-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d48a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d48a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d48a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d48a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d48a-114">See also</span></span>

- [<span data-ttu-id="8d48a-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8d48a-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
