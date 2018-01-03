---
title: "ICorDebugStackWalk::SetContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.SetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00e278df2b23d6fddb18c24eefb3f2aa4d1cc3cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="1c197-102">ICorDebugStackWalk::SetContext 方法</span><span class="sxs-lookup"><span data-stu-id="1c197-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="1c197-103">設定[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件的目前有效的內容執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="1c197-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c197-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c197-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c197-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c197-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="1c197-106">[in]A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)旗標，指出是否已從作用中堆疊框架的內容或回溯堆疊所取得的內容。</span><span class="sxs-lookup"><span data-stu-id="1c197-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="1c197-107">[in]已配置的大小`CONTEXT`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1c197-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="1c197-108">[in]`CONTEXT`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1c197-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c197-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1c197-109">Return Value</span></span>  
 <span data-ttu-id="1c197-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c197-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1c197-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c197-111">HRESULT</span></span>|<span data-ttu-id="1c197-112">描述</span><span class="sxs-lookup"><span data-stu-id="1c197-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c197-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c197-113">S_OK</span></span>|<span data-ttu-id="1c197-114">`ICorDebugStackWalk`成功設定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="1c197-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="1c197-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c197-115">E_FAIL</span></span>|<span data-ttu-id="1c197-116">`ICorDebugStackWalk`未設定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="1c197-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="1c197-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1c197-117">E_INVALIDARG</span></span>|<span data-ttu-id="1c197-118">內容為 null。</span><span class="sxs-lookup"><span data-stu-id="1c197-118">The context is null.</span></span>|  
|<span data-ttu-id="1c197-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="1c197-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="1c197-120">內容緩衝區為太小。</span><span class="sxs-lookup"><span data-stu-id="1c197-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1c197-121">例外狀況</span><span class="sxs-lookup"><span data-stu-id="1c197-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c197-122">備註</span><span class="sxs-lookup"><span data-stu-id="1c197-122">Remarks</span></span>  
 <span data-ttu-id="1c197-123">這個方法不會更改目前執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="1c197-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="1c197-124">將目前的內容設定為無效的內容可能會導致無法預期的結果，堆疊查核器。</span><span class="sxs-lookup"><span data-stu-id="1c197-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="1c197-125">您可以立即呼叫，以擷取此內容的位元完全相同複本[icordebugstackwalk:: Getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1c197-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c197-126">需求</span><span class="sxs-lookup"><span data-stu-id="1c197-126">Requirements</span></span>  
 <span data-ttu-id="1c197-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c197-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c197-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c197-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c197-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c197-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c197-130">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c197-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c197-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c197-131">See Also</span></span>  
 [<span data-ttu-id="1c197-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1c197-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1c197-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="1c197-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
