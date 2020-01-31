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
ms.openlocfilehash: 7318d7d1494b0cf4db54b92ff09775be5500bdb1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869552"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="f7a2a-102">ICorProfilerInfo::GetThreadInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f7a2a-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="f7a2a-103">取得指定之執行緒的目前 Win32 執行緒識別。</span><span class="sxs-lookup"><span data-stu-id="f7a2a-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7a2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7a2a-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7a2a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="f7a2a-106">在要取得其目前 Win32 識別碼之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f7a2a-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="f7a2a-107">脫銷指定執行緒目前 Win32 執行緒識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="f7a2a-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7a2a-108">需求</span><span class="sxs-lookup"><span data-stu-id="f7a2a-108">Requirements</span></span>  
 <span data-ttu-id="f7a2a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7a2a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7a2a-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7a2a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7a2a-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7a2a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7a2a-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7a2a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a2a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a2a-113">See also</span></span>

- [<span data-ttu-id="f7a2a-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f7a2a-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
