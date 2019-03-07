---
title: ICorProfilerCallback::ThreadAssignedToOSThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e955d2fdca67448897ed49b3200542075b4d534
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466774"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="00bd1-102">ICorProfilerCallback::ThreadAssignedToOSThread 方法</span><span class="sxs-lookup"><span data-stu-id="00bd1-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="00bd1-103">通知分析工具正在使用特定的作業系統執行緒實作 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="00bd1-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00bd1-104">語法</span><span class="sxs-lookup"><span data-stu-id="00bd1-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00bd1-105">參數</span><span class="sxs-lookup"><span data-stu-id="00bd1-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="00bd1-106">[in]Managed 執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="00bd1-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="00bd1-107">[in]作業系統執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="00bd1-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00bd1-108">備註</span><span class="sxs-lookup"><span data-stu-id="00bd1-108">Remarks</span></span>  
 <span data-ttu-id="00bd1-109">`ThreadAssignedToOSThread`回呼是否存在，以便分析工具可以維護 fiber 的 managed 執行緒的作業系統執行緒的正確對應。</span><span class="sxs-lookup"><span data-stu-id="00bd1-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00bd1-110">需求</span><span class="sxs-lookup"><span data-stu-id="00bd1-110">Requirements</span></span>  
 <span data-ttu-id="00bd1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00bd1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00bd1-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00bd1-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00bd1-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00bd1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00bd1-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00bd1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bd1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00bd1-115">See also</span></span>
- [<span data-ttu-id="00bd1-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="00bd1-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
