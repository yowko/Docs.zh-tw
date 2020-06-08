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
ms.openlocfilehash: 182a82300183046ccb4a93a79af0dd8f23848c20
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503168"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="a0726-102">ICorProfilerCallback::ThreadAssignedToOSThread 方法</span><span class="sxs-lookup"><span data-stu-id="a0726-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="a0726-103">使用特定的作業系統執行緒，通知分析工具正在執行的受控執行緒。</span><span class="sxs-lookup"><span data-stu-id="a0726-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0726-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0726-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0726-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0726-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="a0726-106">在Managed 執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a0726-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="a0726-107">在作業系統執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a0726-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0726-108">備註</span><span class="sxs-lookup"><span data-stu-id="a0726-108">Remarks</span></span>  
 <span data-ttu-id="a0726-109">`ThreadAssignedToOSThread`回呼存在，讓分析工具能夠在作業系統執行緒的纖程與受控執行緒之間維持精確的對應。</span><span class="sxs-lookup"><span data-stu-id="a0726-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0726-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="a0726-110">Requirements</span></span>  
 <span data-ttu-id="a0726-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0726-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0726-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0726-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0726-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0726-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0726-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0726-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0726-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0726-115">See also</span></span>

- [<span data-ttu-id="a0726-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a0726-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
