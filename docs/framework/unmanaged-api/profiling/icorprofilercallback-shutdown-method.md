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
ms.openlocfilehash: 9761eb5085a77279c4d07d39946a5ad1453ecaaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717221"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="9ecda-102">ICorProfilerCallback::Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="9ecda-102">ICorProfilerCallback::Shutdown Method</span></span>

<span data-ttu-id="9ecda-103">通知 profiler 應用程式正在關閉。</span><span class="sxs-lookup"><span data-stu-id="9ecda-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ecda-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ecda-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9ecda-105">備註</span><span class="sxs-lookup"><span data-stu-id="9ecda-105">Remarks</span></span>  

 <span data-ttu-id="9ecda-106">呼叫方法之後，分析工具程式碼無法安全地呼叫 [ICorProfilerInfo](icorprofilerinfo-interface.md) 介面的方法 `Shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="9ecda-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="9ecda-107">方法的任何呼叫都會 `ICorProfilerInfo` 在方法傳回之後產生未定義的行為 `Shutdown` 。</span><span class="sxs-lookup"><span data-stu-id="9ecda-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="9ecda-108">關機之後可能仍會發生某些不可變的事件;當發生這種情況時，分析工具應該會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="9ecda-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="9ecda-109">`Shutdown`只有當正在剖析的 managed 應用程式是以 managed 程式碼啟動時，才會呼叫此方法 (也就是，進程堆疊上的初始框架是) 管理。</span><span class="sxs-lookup"><span data-stu-id="9ecda-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="9ecda-110">如果應用程式以非受控碼的形式啟動，但稍後跳到 managed 程式碼，則會建立 common language runtime (CLR) 的實例，然後 `Shutdown` 不會呼叫。</span><span class="sxs-lookup"><span data-stu-id="9ecda-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="9ecda-111">在這些情況下，分析工具應該在其程式庫中包含 `DllMain` 使用 DLL_PROCESS_DETACH 值來釋放任何資源，並對其資料執行清除處理的常式，例如將追蹤排清到磁片等等。</span><span class="sxs-lookup"><span data-stu-id="9ecda-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="9ecda-112">一般而言，分析工具必須處理未預期的關機。</span><span class="sxs-lookup"><span data-stu-id="9ecda-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="9ecda-113">例如，Win32 方法可能會暫停進程， `TerminateProcess` (在 Winbase 中宣告) 。</span><span class="sxs-lookup"><span data-stu-id="9ecda-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="9ecda-114">在其他情況下，CLR 會將某些 managed 執行緒 (在背景執行緒) ，而不會為它們提供有條理的損毀訊息。</span><span class="sxs-lookup"><span data-stu-id="9ecda-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ecda-115">需求</span><span class="sxs-lookup"><span data-stu-id="9ecda-115">Requirements</span></span>  

 <span data-ttu-id="9ecda-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecda-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ecda-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ecda-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ecda-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ecda-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ecda-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ecda-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecda-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecda-120">See also</span></span>

- [<span data-ttu-id="9ecda-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9ecda-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9ecda-122">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="9ecda-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)
