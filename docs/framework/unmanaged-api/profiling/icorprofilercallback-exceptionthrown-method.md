---
title: ICorProfilerCallback::ExceptionThrown 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9cdbc2234519c0dba1a5004246492e7609ea2b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597891"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="6aeef-102">ICorProfilerCallback::ExceptionThrown 方法</span><span class="sxs-lookup"><span data-stu-id="6aeef-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="6aeef-103">通知分析工具已擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6aeef-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6aeef-104">只有當例外狀況到達 managed 程式碼，會呼叫此函數。</span><span class="sxs-lookup"><span data-stu-id="6aeef-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aeef-105">語法</span><span class="sxs-lookup"><span data-stu-id="6aeef-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aeef-106">參數</span><span class="sxs-lookup"><span data-stu-id="6aeef-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="6aeef-107">[in]導致擲回例外狀況物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6aeef-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aeef-108">備註</span><span class="sxs-lookup"><span data-stu-id="6aeef-108">Remarks</span></span>  
 <span data-ttu-id="6aeef-109">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="6aeef-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="6aeef-110">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="6aeef-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="6aeef-111">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="6aeef-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aeef-112">需求</span><span class="sxs-lookup"><span data-stu-id="6aeef-112">Requirements</span></span>  
 <span data-ttu-id="6aeef-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6aeef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aeef-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6aeef-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6aeef-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aeef-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aeef-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aeef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aeef-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aeef-117">See also</span></span>

- [<span data-ttu-id="6aeef-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6aeef-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
