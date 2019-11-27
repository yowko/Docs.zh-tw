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
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446938"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="1674c-102">ICorProfilerCallback::Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="1674c-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="1674c-103">通知 profiler 應用程式正在關閉。</span><span class="sxs-lookup"><span data-stu-id="1674c-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1674c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1674c-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1674c-105">備註</span><span class="sxs-lookup"><span data-stu-id="1674c-105">Remarks</span></span>  
 <span data-ttu-id="1674c-106">呼叫 `Shutdown` 方法之後，分析工具程式碼無法安全地呼叫[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面的方法。</span><span class="sxs-lookup"><span data-stu-id="1674c-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="1674c-107">`ICorProfilerInfo` 方法的任何呼叫都會在 `Shutdown` 方法傳回之後導致未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="1674c-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="1674c-108">某些不可變事件在關機後可能仍會發生;分析工具應該小心在發生這種情況時立即傳回。</span><span class="sxs-lookup"><span data-stu-id="1674c-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="1674c-109">只有當正在分析的 managed 應用程式啟動為受控碼（也就是管理進程堆疊上的初始框架）時，才會呼叫 `Shutdown` 方法。</span><span class="sxs-lookup"><span data-stu-id="1674c-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="1674c-110">如果應用程式是以非受控碼啟動，但之後跳到 managed 程式碼，藉此建立 common language runtime （CLR）的實例，則不會呼叫 `Shutdown`。</span><span class="sxs-lookup"><span data-stu-id="1674c-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="1674c-111">在這些情況下，分析工具應該包含在其程式庫中的 `DllMain` 常式，其中使用 DLL_PROCESS_DETACH 值來釋放任何資源，並執行其資料的清除處理，例如將追蹤排清到磁片等等。</span><span class="sxs-lookup"><span data-stu-id="1674c-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="1674c-112">一般來說，分析工具必須處理非預期的關機。</span><span class="sxs-lookup"><span data-stu-id="1674c-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="1674c-113">例如，Win32 `TerminateProcess` 方法（在 Winbase 中宣告）可能會暫停處理常式。</span><span class="sxs-lookup"><span data-stu-id="1674c-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="1674c-114">在其他情況下，CLR 將會停止特定的 managed 執行緒（背景執行緒），而不會為它們傳遞有序的析構訊息。</span><span class="sxs-lookup"><span data-stu-id="1674c-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1674c-115">需求</span><span class="sxs-lookup"><span data-stu-id="1674c-115">Requirements</span></span>  
 <span data-ttu-id="1674c-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1674c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1674c-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1674c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1674c-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1674c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1674c-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1674c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1674c-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="1674c-120">See also</span></span>

- [<span data-ttu-id="1674c-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1674c-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1674c-122">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="1674c-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
