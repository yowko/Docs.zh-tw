---
title: ICorDebugStackWalk::SetContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6eb97fc70fec25f4b225c3fd5bad1e780091f7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771031"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="8c54b-102">ICorDebugStackWalk::SetContext 方法</span><span class="sxs-lookup"><span data-stu-id="8c54b-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="8c54b-103">設定組[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)有效的內容執行緒物件的目前內容。</span><span class="sxs-lookup"><span data-stu-id="8c54b-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c54b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c54b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c54b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c54b-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="8c54b-106">[in]A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)旗標，指出內容是從使用中框架在堆疊上，還是回溯堆疊所取得的內容。</span><span class="sxs-lookup"><span data-stu-id="8c54b-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8c54b-107">[in]配置的大小`CONTEXT`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8c54b-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="8c54b-108">[in]`CONTEXT`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8c54b-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c54b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c54b-109">Return Value</span></span>  
 <span data-ttu-id="8c54b-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c54b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8c54b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c54b-111">HRESULT</span></span>|<span data-ttu-id="8c54b-112">描述</span><span class="sxs-lookup"><span data-stu-id="8c54b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c54b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c54b-113">S_OK</span></span>|<span data-ttu-id="8c54b-114">`ICorDebugStackWalk`成功設定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="8c54b-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="8c54b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c54b-115">E_FAIL</span></span>|<span data-ttu-id="8c54b-116">`ICorDebugStackWalk`未設定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="8c54b-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="8c54b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8c54b-117">E_INVALIDARG</span></span>|<span data-ttu-id="8c54b-118">內容為 null。</span><span class="sxs-lookup"><span data-stu-id="8c54b-118">The context is null.</span></span>|  
|<span data-ttu-id="8c54b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="8c54b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="8c54b-120">內容緩衝區是太小。</span><span class="sxs-lookup"><span data-stu-id="8c54b-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8c54b-121">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8c54b-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c54b-122">備註</span><span class="sxs-lookup"><span data-stu-id="8c54b-122">Remarks</span></span>  
 <span data-ttu-id="8c54b-123">這個方法不會更改目前執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="8c54b-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="8c54b-124">將目前的內容設定為無效的內容可能會導致無法預期的結果從堆疊查核器。</span><span class="sxs-lookup"><span data-stu-id="8c54b-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="8c54b-125">您可以擷取的位元的確切複本，此內容的立即呼叫[icordebugstackwalk:: Getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8c54b-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c54b-126">需求</span><span class="sxs-lookup"><span data-stu-id="8c54b-126">Requirements</span></span>  
 <span data-ttu-id="8c54b-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c54b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c54b-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c54b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c54b-129">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c54b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c54b-130">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c54b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c54b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c54b-131">See also</span></span>

- [<span data-ttu-id="8c54b-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8c54b-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8c54b-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="8c54b-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
