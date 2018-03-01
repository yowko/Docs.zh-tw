---
title: "ICorProfilerCallback::UnmanagedToManagedTransition 方法"
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
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1653a92563f0031fcb4c215dd58e4e1ac73030d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="7ab89-102">ICorProfilerCallback::UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="7ab89-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="7ab89-103">通知分析工具，從 unmanaged 程式碼轉換為 managed 程式碼已發生。</span><span class="sxs-lookup"><span data-stu-id="7ab89-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab89-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ab89-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ab89-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ab89-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7ab89-106">[in]所呼叫之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ab89-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="7ab89-107">[in]值為[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)指出轉換是發生由於 unmanaged 程式碼呼叫至 managed 程式碼，或因為從受管理的一個由呼叫 unmanaged 函式傳回的列舉。</span><span class="sxs-lookup"><span data-stu-id="7ab89-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab89-108">備註</span><span class="sxs-lookup"><span data-stu-id="7ab89-108">Remarks</span></span>  
 <span data-ttu-id="7ab89-109">如果值`reason`是 COR_PRF_TRANSITION_RETURN 和`functionId`不是 null，函式識別碼就是 unmanaged 的函式，並將永遠不會有已編譯使用在 just-in-time (JIT) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="7ab89-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="7ab89-110">Unmanaged 函式有與其相關聯，例如名稱及一些中繼資料的一些基本資訊。</span><span class="sxs-lookup"><span data-stu-id="7ab89-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="7ab89-111">如果值`reason`是 COR_PRF_TRANSITION_CALL，這可能會出現，呼叫的函式 （亦即，managed 函式） 尚未被 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="7ab89-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab89-112">需求</span><span class="sxs-lookup"><span data-stu-id="7ab89-112">Requirements</span></span>  
 <span data-ttu-id="7ab89-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab89-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab89-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ab89-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ab89-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ab89-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ab89-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab89-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab89-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ab89-117">See Also</span></span>  
 [<span data-ttu-id="7ab89-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7ab89-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7ab89-119">ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="7ab89-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [<span data-ttu-id="7ab89-120">在 C++ 中使用明確的 PInvoke (DllImport 屬性)</span><span class="sxs-lookup"><span data-stu-id="7ab89-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [<span data-ttu-id="7ab89-121">使用 C++ Interop (隱含 PInvoke)</span><span class="sxs-lookup"><span data-stu-id="7ab89-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
