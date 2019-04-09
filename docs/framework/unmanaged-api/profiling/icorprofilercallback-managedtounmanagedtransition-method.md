---
title: ICorProfilerCallback::ManagedToUnmanagedTransition 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b00394d0b08e7e4a02b95437908dd65a51d0a042
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084605"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="7a0ac-102">ICorProfilerCallback::ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="7a0ac-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="7a0ac-103">通知發生從 managed 程式碼轉換到 unmanaged 程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a0ac-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a0ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a0ac-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7a0ac-106">[in]正在呼叫函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="7a0ac-107">[in]值為[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)列舉，指出轉換是否發生因為呼叫 unmanaged 程式碼從 managed 程式碼，或因為由未受管理的一個呼叫 managed 函式傳回。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a0ac-108">備註</span><span class="sxs-lookup"><span data-stu-id="7a0ac-108">Remarks</span></span>  
 <span data-ttu-id="7a0ac-109">如果值`reason`是 COR_PRF_TRANSITION_CALL，識別碼是，unmanaged 的函式，將永遠不會已編譯使用-just-in-time 編譯器函式。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="7a0ac-110">Unmanaged 函式有與其相關聯，例如名稱及一些中繼資料的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="7a0ac-111">如果 unmanaged 函式呼叫使用隱含的平台叫用 (PInvoke)，執行階段無法判斷呼叫的目的地，而`functionId`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="7a0ac-112">如需有關隱含 PInvoke 的詳細資訊，請參閱 <<c0> [ 使用 c + + Interop (隱含 PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a0ac-113">需求</span><span class="sxs-lookup"><span data-stu-id="7a0ac-113">Requirements</span></span>  
 <span data-ttu-id="7a0ac-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a0ac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0ac-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a0ac-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a0ac-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a0ac-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7a0ac-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7a0ac-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a0ac-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a0ac-118">See also</span></span>

- [<span data-ttu-id="7a0ac-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7a0ac-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7a0ac-120">UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="7a0ac-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="7a0ac-121">在 C++ 中使用明確的 PInvoke (DllImport 屬性)</span><span class="sxs-lookup"><span data-stu-id="7a0ac-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
