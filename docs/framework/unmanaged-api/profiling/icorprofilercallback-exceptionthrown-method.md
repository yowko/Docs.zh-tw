---
title: "ICorProfilerCallback::ExceptionThrown 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65fdd8f2912dc2854ba7801244ba489426d05e47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="b77cc-102">ICorProfilerCallback::ExceptionThrown 方法</span><span class="sxs-lookup"><span data-stu-id="b77cc-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="b77cc-103">通知分析工具已擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b77cc-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b77cc-104">例外狀況到達 managed 程式碼時，才會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="b77cc-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b77cc-105">語法</span><span class="sxs-lookup"><span data-stu-id="b77cc-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b77cc-106">參數</span><span class="sxs-lookup"><span data-stu-id="b77cc-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="b77cc-107">[in]導致擲回例外狀況物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b77cc-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b77cc-108">備註</span><span class="sxs-lookup"><span data-stu-id="b77cc-108">Remarks</span></span>  
 <span data-ttu-id="b77cc-109">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b77cc-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b77cc-110">如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="b77cc-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b77cc-111">Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="b77cc-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b77cc-112">需求</span><span class="sxs-lookup"><span data-stu-id="b77cc-112">Requirements</span></span>  
 <span data-ttu-id="b77cc-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b77cc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b77cc-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b77cc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b77cc-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b77cc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b77cc-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b77cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77cc-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="b77cc-117">See Also</span></span>  
 [<span data-ttu-id="b77cc-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b77cc-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
