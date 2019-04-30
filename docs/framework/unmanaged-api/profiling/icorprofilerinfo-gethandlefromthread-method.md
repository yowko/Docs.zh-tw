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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fc26ad9b25ad243bf868d6ef3155360509e6483
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049579"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="ac4f4-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="ac4f4-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="ac4f4-103">會對應至 Win32 執行緒控制代碼之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac4f4-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac4f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac4f4-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac4f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac4f4-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ac4f4-106">[in]要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac4f4-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="ac4f4-107">[out]Win32 執行緒控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="ac4f4-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac4f4-108">備註</span><span class="sxs-lookup"><span data-stu-id="ac4f4-108">Remarks</span></span>  
 <span data-ttu-id="ac4f4-109">分析工具必須呼叫 Win32`DuplicateHandle`後才能使用它的控制代碼上的函式。</span><span class="sxs-lookup"><span data-stu-id="ac4f4-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac4f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="ac4f4-110">Requirements</span></span>  
 <span data-ttu-id="ac4f4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac4f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac4f4-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac4f4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac4f4-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac4f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac4f4-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac4f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac4f4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac4f4-115">See also</span></span>

- [<span data-ttu-id="ac4f4-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ac4f4-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
