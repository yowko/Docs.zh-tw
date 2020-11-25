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
ms.openlocfilehash: 2d6f34d88dd79fe350f1c018e3afa55e5b180c46
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731997"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="ea695-102">ICorProfilerCallback::ThreadAssignedToOSThread 方法</span><span class="sxs-lookup"><span data-stu-id="ea695-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>

<span data-ttu-id="ea695-103">通知分析工具正在使用特定的作業系統執行緒來執行 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="ea695-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea695-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea695-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea695-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea695-105">Parameters</span></span>  

 `managedThreadId`  
 <span data-ttu-id="ea695-106">在Managed 執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ea695-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="ea695-107">在作業系統執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ea695-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea695-108">備註</span><span class="sxs-lookup"><span data-stu-id="ea695-108">Remarks</span></span>  

 <span data-ttu-id="ea695-109">`ThreadAssignedToOSThread`回呼已存在，讓分析工具可以在作業系統執行緒的纖程和 managed 執行緒之間保持精確的對應。</span><span class="sxs-lookup"><span data-stu-id="ea695-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea695-110">需求</span><span class="sxs-lookup"><span data-stu-id="ea695-110">Requirements</span></span>  

 <span data-ttu-id="ea695-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea695-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea695-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea695-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea695-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea695-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea695-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea695-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea695-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea695-115">See also</span></span>

- [<span data-ttu-id="ea695-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ea695-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
