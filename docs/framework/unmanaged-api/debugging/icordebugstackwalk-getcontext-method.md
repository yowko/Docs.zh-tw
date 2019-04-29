---
title: ICorDebugStackWalk::GetContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba1e6c113fb4caa0db8963e238d3eceba0cc8ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782742"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="6f142-102">ICorDebugStackWalk::GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="6f142-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="6f142-103">傳回目前的框架的內容[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="6f142-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f142-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f142-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f142-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f142-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="6f142-106">[in]旗標，表示要求 （在 WinNT.h 中定義） 的內容緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="6f142-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="6f142-107">[in]內容緩衝區配置的大小。</span><span class="sxs-lookup"><span data-stu-id="6f142-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6f142-108">[out]內容的實際大小。</span><span class="sxs-lookup"><span data-stu-id="6f142-108">[out] The actual size of the context.</span></span> <span data-ttu-id="6f142-109">此值必須小於或等於內容緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="6f142-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="6f142-110">[out]內容的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6f142-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f142-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f142-111">Return Value</span></span>  
 <span data-ttu-id="6f142-112">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f142-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6f142-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f142-113">HRESULT</span></span>|<span data-ttu-id="6f142-114">描述</span><span class="sxs-lookup"><span data-stu-id="6f142-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f142-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f142-115">S_OK</span></span>|<span data-ttu-id="6f142-116">已成功地傳回目前的框架的內容。</span><span class="sxs-lookup"><span data-stu-id="6f142-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="6f142-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f142-117">E_FAIL</span></span>|<span data-ttu-id="6f142-118">無法傳回內容。</span><span class="sxs-lookup"><span data-stu-id="6f142-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="6f142-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="6f142-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="6f142-120">內容緩衝區是太小。</span><span class="sxs-lookup"><span data-stu-id="6f142-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="6f142-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="6f142-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="6f142-122">框架指標已經結尾的堆疊;因此，可以不存取任何其他的框架。</span><span class="sxs-lookup"><span data-stu-id="6f142-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6f142-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="6f142-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f142-124">備註</span><span class="sxs-lookup"><span data-stu-id="6f142-124">Remarks</span></span>  
 <span data-ttu-id="6f142-125">因為回溯還原暫存器，例如靜態暫存器中，只有部分內容可能不完全符合的註冊狀態時呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f142-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f142-126">需求</span><span class="sxs-lookup"><span data-stu-id="6f142-126">Requirements</span></span>  
 <span data-ttu-id="6f142-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f142-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f142-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f142-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f142-129">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f142-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f142-130">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f142-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f142-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f142-131">See also</span></span>

- [<span data-ttu-id="6f142-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6f142-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6f142-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="6f142-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
