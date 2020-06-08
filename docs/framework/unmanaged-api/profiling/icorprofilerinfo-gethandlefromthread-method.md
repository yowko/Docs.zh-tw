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
ms.openlocfilehash: 419195d9450bf07e5ad8c7cedcac76e175137c96
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498176"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="bd3d4-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="bd3d4-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="bd3d4-103">將執行緒的識別碼對應至 Win32 執行緒控制碼。</span><span class="sxs-lookup"><span data-stu-id="bd3d4-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd3d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd3d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd3d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd3d4-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="bd3d4-106">在要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="bd3d4-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="bd3d4-107">脫銷Win32 執行緒控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="bd3d4-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd3d4-108">備註</span><span class="sxs-lookup"><span data-stu-id="bd3d4-108">Remarks</span></span>  
 <span data-ttu-id="bd3d4-109">分析工具必須先呼叫控制碼上的 Win32 函式， `DuplicateHandle` 才能使用它。</span><span class="sxs-lookup"><span data-stu-id="bd3d4-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd3d4-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="bd3d4-110">Requirements</span></span>  
 <span data-ttu-id="bd3d4-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd3d4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd3d4-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd3d4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd3d4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd3d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd3d4-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd3d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd3d4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd3d4-115">See also</span></span>

- [<span data-ttu-id="bd3d4-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bd3d4-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
