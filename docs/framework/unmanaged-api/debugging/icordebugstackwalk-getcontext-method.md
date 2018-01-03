---
title: "ICorDebugStackWalk::GetContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 080ce39422faee4e1228bd87bf994080fab4de71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="3c130-102">ICorDebugStackWalk::GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="3c130-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="3c130-103">傳回目前的框架中的內容[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="3c130-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c130-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c130-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c130-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c130-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="3c130-106">[in]旗標，表示要求 （在 WinNT.h 中定義） 的內容緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="3c130-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="3c130-107">[in]內容緩衝區配置的大小。</span><span class="sxs-lookup"><span data-stu-id="3c130-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="3c130-108">[out]內容的實際大小。</span><span class="sxs-lookup"><span data-stu-id="3c130-108">[out] The actual size of the context.</span></span> <span data-ttu-id="3c130-109">此值必須小於或等於內容緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="3c130-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="3c130-110">[out]內容的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3c130-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c130-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c130-111">Return Value</span></span>  
 <span data-ttu-id="3c130-112">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c130-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3c130-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c130-113">HRESULT</span></span>|<span data-ttu-id="3c130-114">描述</span><span class="sxs-lookup"><span data-stu-id="3c130-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c130-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c130-115">S_OK</span></span>|<span data-ttu-id="3c130-116">目前畫面格的內容已成功地傳回。</span><span class="sxs-lookup"><span data-stu-id="3c130-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="3c130-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c130-117">E_FAIL</span></span>|<span data-ttu-id="3c130-118">不會傳回內容。</span><span class="sxs-lookup"><span data-stu-id="3c130-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="3c130-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="3c130-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="3c130-120">內容緩衝區為太小。</span><span class="sxs-lookup"><span data-stu-id="3c130-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="3c130-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="3c130-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="3c130-122">框架指標已經結尾的堆疊。因此，沒有其他框架則可以存取。</span><span class="sxs-lookup"><span data-stu-id="3c130-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3c130-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="3c130-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c130-124">備註</span><span class="sxs-lookup"><span data-stu-id="3c130-124">Remarks</span></span>  
 <span data-ttu-id="3c130-125">回溯還原子集暫存器，例如非暫時性暫存器，因為內容可能不完全與暫存狀態時呼叫。</span><span class="sxs-lookup"><span data-stu-id="3c130-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c130-126">需求</span><span class="sxs-lookup"><span data-stu-id="3c130-126">Requirements</span></span>  
 <span data-ttu-id="3c130-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c130-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c130-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c130-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c130-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c130-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c130-130">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c130-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c130-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c130-131">See Also</span></span>  
 [<span data-ttu-id="3c130-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3c130-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3c130-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="3c130-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
