---
title: ICorProfilerCallback::UnmanagedToManagedTransition 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 446de663d437c950f3a9be968e7dcbe8d25ed2b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717228"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="979b8-102">ICorProfilerCallback::UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="979b8-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>

<span data-ttu-id="979b8-103">通知分析工具，從非受控程式碼轉換成 managed 程式碼時發生。</span><span class="sxs-lookup"><span data-stu-id="979b8-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="979b8-104">語法</span><span class="sxs-lookup"><span data-stu-id="979b8-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="979b8-105">參數</span><span class="sxs-lookup"><span data-stu-id="979b8-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="979b8-106">在正在呼叫之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="979b8-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="979b8-107">在 [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 列舉值，這個值會指出是否因為從非受控程式碼的 managed 程式碼呼叫，或由 managed 函式所呼叫的非受控函式傳回而發生轉換。</span><span class="sxs-lookup"><span data-stu-id="979b8-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="979b8-108">備註</span><span class="sxs-lookup"><span data-stu-id="979b8-108">Remarks</span></span>  

 <span data-ttu-id="979b8-109">如果的值 `reason` 是 COR_PRF_TRANSITION_RETURN 而不 `functionId` 是 null，則函式識別碼就是非受控函式的識別碼，而且永遠不會使用即時 (JIT) 編譯器進行編譯。</span><span class="sxs-lookup"><span data-stu-id="979b8-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="979b8-110">非受控函式有一些相關聯的基本資訊，例如名稱和一些中繼資料。</span><span class="sxs-lookup"><span data-stu-id="979b8-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="979b8-111">如果的值 `reason` 是 COR_PRF_TRANSITION_CALL，則呼叫的函式可能會 (也可能是 managed 函式) 尚未 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="979b8-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="979b8-112">需求</span><span class="sxs-lookup"><span data-stu-id="979b8-112">Requirements</span></span>  

 <span data-ttu-id="979b8-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="979b8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="979b8-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="979b8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="979b8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="979b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="979b8-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="979b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979b8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="979b8-117">See also</span></span>

- [<span data-ttu-id="979b8-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="979b8-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="979b8-119">ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="979b8-119">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="979b8-120">在 c + + 中使用明確的 PInvoke (DllImport 屬性) </span><span class="sxs-lookup"><span data-stu-id="979b8-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="979b8-121">使用 c + + Interop (隱含 PInvoke) </span><span class="sxs-lookup"><span data-stu-id="979b8-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
