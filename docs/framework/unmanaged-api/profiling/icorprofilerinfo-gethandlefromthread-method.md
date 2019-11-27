---
title: ICorProfilerInfo::GetHandleFromThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: e508ccd81d25aa3d303456fa88554903ec71d633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439060"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="70bb5-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="70bb5-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="70bb5-103">將執行緒的識別碼對應至 Win32 執行緒控制碼。</span><span class="sxs-lookup"><span data-stu-id="70bb5-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70bb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="70bb5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70bb5-105">參數</span><span class="sxs-lookup"><span data-stu-id="70bb5-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="70bb5-106">在要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="70bb5-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="70bb5-107">脫銷Win32 執行緒控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="70bb5-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70bb5-108">備註</span><span class="sxs-lookup"><span data-stu-id="70bb5-108">Remarks</span></span>  
 <span data-ttu-id="70bb5-109">分析工具必須先呼叫控制碼上的 Win32 `DuplicateHandle` 函式，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="70bb5-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70bb5-110">需求</span><span class="sxs-lookup"><span data-stu-id="70bb5-110">Requirements</span></span>  
 <span data-ttu-id="70bb5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70bb5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70bb5-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70bb5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70bb5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70bb5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70bb5-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70bb5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bb5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="70bb5-115">See also</span></span>

- [<span data-ttu-id="70bb5-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="70bb5-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
