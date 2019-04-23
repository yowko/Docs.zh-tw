---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 305c8c7abf778ea68efe06f3bdb57af001ea1b9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227707"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="67a59-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="67a59-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="67a59-103">通知分析工具的例外狀況處理回溯階段已完成回溯函式。</span><span class="sxs-lookup"><span data-stu-id="67a59-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a59-104">語法</span><span class="sxs-lookup"><span data-stu-id="67a59-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="67a59-105">備註</span><span class="sxs-lookup"><span data-stu-id="67a59-105">Remarks</span></span>  
 <span data-ttu-id="67a59-106">當`ExceptionUnwindFunctionLeave`呼叫方法，會從堆疊移除函式執行個體和其堆疊資料。</span><span class="sxs-lookup"><span data-stu-id="67a59-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="67a59-107">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在此呼叫期間封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="67a59-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="67a59-108">如果嘗試此程式碼剖析工具封鎖和進行記憶體回收，則執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="67a59-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="67a59-109">此外，此呼叫期間，分析工具必須呼叫至 managed 程式碼，或以任何方式造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="67a59-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a59-110">需求</span><span class="sxs-lookup"><span data-stu-id="67a59-110">Requirements</span></span>  
 <span data-ttu-id="67a59-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67a59-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a59-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67a59-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67a59-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67a59-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67a59-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a59-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67a59-115">See also</span></span>

- [<span data-ttu-id="67a59-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="67a59-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="67a59-117">ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="67a59-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
