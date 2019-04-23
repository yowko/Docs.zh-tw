---
title: ICorProfilerCallback::Shutdown 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192637"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="40314-102">ICorProfilerCallback::Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="40314-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="40314-103">通知應用程式正在關閉分析工具。</span><span class="sxs-lookup"><span data-stu-id="40314-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40314-104">語法</span><span class="sxs-lookup"><span data-stu-id="40314-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="40314-105">備註</span><span class="sxs-lookup"><span data-stu-id="40314-105">Remarks</span></span>  
 <span data-ttu-id="40314-106">分析工具程式碼無法安全地呼叫方法[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面之後`Shutdown`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="40314-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="40314-107">呼叫任何`ICorProfilerInfo`方法會導致未定義的行為之後,`Shutdown`方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="40314-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="40314-108">特定的不可變事件仍然可能發生之後關機;分析工具應該謹慎地發生這種情況時，立即傳回。</span><span class="sxs-lookup"><span data-stu-id="40314-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="40314-109">`Shutdown`正在分析 managed 應用程式啟動為 managed 程式碼時，才會呼叫方法 （也就是初始堆疊上的框架處理程序管理）。</span><span class="sxs-lookup"><span data-stu-id="40314-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="40314-110">如果應用程式啟動為 unmanaged 程式碼，但稍後開始運用 managed 程式碼，藉此建立的執行個體的 common language runtime (CLR)，然後`Shutdown`將不會呼叫。</span><span class="sxs-lookup"><span data-stu-id="40314-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="40314-111">在這些情況下，分析工具應該在其文件庫中包含`DllMain`釋放任何資源，並執行清除其資料，例如排清到磁碟等的追蹤處理常式，它會使用 DLL_PROCESS_DETACH 值。</span><span class="sxs-lookup"><span data-stu-id="40314-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="40314-112">一般情況下，分析工具必須應付非預期的關機。</span><span class="sxs-lookup"><span data-stu-id="40314-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="40314-113">比方說，可能會停止處理程序的 Win32 的`TerminateProcess`（Winbase.h 中宣告） 的方法。</span><span class="sxs-lookup"><span data-stu-id="40314-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="40314-114">在其他情況下，CLR 將會中止特定 managed 的執行緒 （背景執行緒），而不進行有條理的解構郵件傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="40314-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40314-115">需求</span><span class="sxs-lookup"><span data-stu-id="40314-115">Requirements</span></span>  
 <span data-ttu-id="40314-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40314-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40314-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40314-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40314-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40314-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40314-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40314-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40314-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40314-120">See also</span></span>

- [<span data-ttu-id="40314-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="40314-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="40314-122">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="40314-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
