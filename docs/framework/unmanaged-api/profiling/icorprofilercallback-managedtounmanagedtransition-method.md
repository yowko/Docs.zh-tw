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
ms.openlocfilehash: f4f5871bdd7adf11fcc811fd40c62e3027b8e607
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426183"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="11215-102">ICorProfilerCallback::ManagedToUnmanagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="11215-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="11215-103">通知分析工具，已發生從 managed 程式碼到未受管理程式碼的轉換。</span><span class="sxs-lookup"><span data-stu-id="11215-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11215-104">語法</span><span class="sxs-lookup"><span data-stu-id="11215-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11215-105">參數</span><span class="sxs-lookup"><span data-stu-id="11215-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="11215-106">在所呼叫之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="11215-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="11215-107">在[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)列舉的值，指出轉換是否因為從 managed 程式碼呼叫非受控碼而發生，或是因為非受控函式所呼叫的 managed 函數傳回。</span><span class="sxs-lookup"><span data-stu-id="11215-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11215-108">備註</span><span class="sxs-lookup"><span data-stu-id="11215-108">Remarks</span></span>  
 <span data-ttu-id="11215-109">如果 `reason` 的值為 COR_PRF_TRANSITION_CALL，則函式識別碼就是不會使用即時編譯器編譯的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="11215-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="11215-110">非受控函式具有與其相關聯的基本資訊，例如名稱和一些中繼資料。</span><span class="sxs-lookup"><span data-stu-id="11215-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="11215-111">如果使用隱含平台叫用（PInvoke）呼叫了非受控函式，執行時間就無法判斷呼叫的目的地，而 `functionId` 的值將會是 null。</span><span class="sxs-lookup"><span data-stu-id="11215-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="11215-112">如需隱含 PInvoke 的詳細資訊，請參閱[使用C++ Interop （隱含 pinvoke）](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。</span><span class="sxs-lookup"><span data-stu-id="11215-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11215-113">需求</span><span class="sxs-lookup"><span data-stu-id="11215-113">Requirements</span></span>  
 <span data-ttu-id="11215-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11215-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11215-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11215-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11215-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11215-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11215-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11215-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11215-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11215-118">See also</span></span>

- [<span data-ttu-id="11215-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="11215-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="11215-120">UnmanagedToManagedTransition 方法</span><span class="sxs-lookup"><span data-stu-id="11215-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="11215-121">在 C++ 中使用明確的 PInvoke (DllImport 屬性)</span><span class="sxs-lookup"><span data-stu-id="11215-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
