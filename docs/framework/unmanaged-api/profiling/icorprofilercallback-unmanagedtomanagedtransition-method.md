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
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439900"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="53c70-102">ICorProfilerCallback::UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="53c70-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="53c70-103">通知分析工具，已發生從非受控碼到 managed 程式碼的轉換。</span><span class="sxs-lookup"><span data-stu-id="53c70-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c70-104">語法</span><span class="sxs-lookup"><span data-stu-id="53c70-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53c70-105">參數</span><span class="sxs-lookup"><span data-stu-id="53c70-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="53c70-106">在所呼叫之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="53c70-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="53c70-107">在[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)列舉的值，指出轉換是因為來自非受控程式碼的 managed 程式碼呼叫，還是因為由 managed 函式所呼叫的非受控函數傳回而發生。</span><span class="sxs-lookup"><span data-stu-id="53c70-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53c70-108">備註</span><span class="sxs-lookup"><span data-stu-id="53c70-108">Remarks</span></span>  
 <span data-ttu-id="53c70-109">如果 `reason` 的值為 COR_PRF_TRANSITION_RETURN 且 `functionId` 不是 null，則函式識別碼會是非受控函式的 ID，而且永遠不會使用即時（JIT）編譯器來編譯。</span><span class="sxs-lookup"><span data-stu-id="53c70-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="53c70-110">非受控函式有一些與其相關聯的基本資訊，例如名稱和一些中繼資料。</span><span class="sxs-lookup"><span data-stu-id="53c70-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="53c70-111">如果 `reason` 的值為 COR_PRF_TRANSITION_CALL，則可能是被呼叫的函式（也就是 managed 函數）尚未進行 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="53c70-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53c70-112">需求</span><span class="sxs-lookup"><span data-stu-id="53c70-112">Requirements</span></span>  
 <span data-ttu-id="53c70-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53c70-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c70-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53c70-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53c70-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53c70-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53c70-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c70-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c70-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="53c70-117">See also</span></span>

- [<span data-ttu-id="53c70-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="53c70-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="53c70-119">ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="53c70-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="53c70-120">在 C++ 中使用明確的 PInvoke (DllImport 屬性)</span><span class="sxs-lookup"><span data-stu-id="53c70-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="53c70-121">使用 C++ Interop (隱含 PInvoke)</span><span class="sxs-lookup"><span data-stu-id="53c70-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
