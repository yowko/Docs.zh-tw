---
title: ICorProfilerInfo::GetThreadInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 5edc4e0e2fc25ddae6ccabc1aa9c9a031292b63a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449886"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="c5a16-102">ICorProfilerInfo::GetThreadInfo 方法</span><span class="sxs-lookup"><span data-stu-id="c5a16-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="c5a16-103">Gets the current Win32 thread identity for the specified thread.</span><span class="sxs-lookup"><span data-stu-id="c5a16-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a16-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5a16-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5a16-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5a16-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c5a16-106">[in] The ID of the thread for which to get the current Win32 ID.</span><span class="sxs-lookup"><span data-stu-id="c5a16-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="c5a16-107">[out] A pointer to the specified thread's current Win32 thread ID.</span><span class="sxs-lookup"><span data-stu-id="c5a16-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a16-108">需求</span><span class="sxs-lookup"><span data-stu-id="c5a16-108">Requirements</span></span>  
 <span data-ttu-id="c5a16-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5a16-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a16-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5a16-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5a16-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5a16-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5a16-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a16-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a16-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5a16-113">See also</span></span>

- [<span data-ttu-id="c5a16-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c5a16-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
