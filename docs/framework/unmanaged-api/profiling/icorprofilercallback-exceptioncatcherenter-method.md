---
title: ICorProfilerCallback::ExceptionCatcherEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb31da8b3fb9148bb41cf7216b44e7cbf610eaee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671612"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="1fe8f-102">ICorProfilerCallback::ExceptionCatcherEnter 方法</span><span class="sxs-lookup"><span data-stu-id="1fe8f-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="1fe8f-103">通知控制項已傳遞至適當的分析工具`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fe8f-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fe8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="1fe8f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1fe8f-106">[in]包含的函式的識別項`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="1fe8f-107">[in]正在處理的例外狀況的識別項。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fe8f-108">備註</span><span class="sxs-lookup"><span data-stu-id="1fe8f-108">Remarks</span></span>  
 <span data-ttu-id="1fe8f-109">`ExceptionCatcherEnter`只有 catch 點是在 just-in-time (JIT) 編譯器編譯的程式碼呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="1fe8f-110">在 unmanaged 程式碼，或執行階段內部的程式碼中攔截到例外狀況不會呼叫這項通知。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="1fe8f-111">`objectId`值會傳遞一次進行記憶體回收可能移因為物件由於`ExceptionThrown`通知。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="1fe8f-112">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1fe8f-113">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1fe8f-114">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe8f-115">需求</span><span class="sxs-lookup"><span data-stu-id="1fe8f-115">Requirements</span></span>  
 <span data-ttu-id="1fe8f-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1fe8f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fe8f-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1fe8f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fe8f-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fe8f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fe8f-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fe8f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe8f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fe8f-120">See also</span></span>
- [<span data-ttu-id="1fe8f-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1fe8f-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1fe8f-122">ExceptionCatcherLeave 方法</span><span class="sxs-lookup"><span data-stu-id="1fe8f-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
