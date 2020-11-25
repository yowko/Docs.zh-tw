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
ms.openlocfilehash: 927f2077b4bb71177c24816774d06643ebdaa922
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711958"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="58886-102">ICorDebugStackWalk::GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="58886-102">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="58886-103">傳回 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 物件中目前框架的內容。</span><span class="sxs-lookup"><span data-stu-id="58886-103">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58886-104">語法</span><span class="sxs-lookup"><span data-stu-id="58886-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58886-105">參數</span><span class="sxs-lookup"><span data-stu-id="58886-105">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="58886-106">在旗標，指出 (在 WinNT) 中定義之內容緩衝區的要求內容。</span><span class="sxs-lookup"><span data-stu-id="58886-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="58886-107">在內容緩衝區的配置大小。</span><span class="sxs-lookup"><span data-stu-id="58886-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="58886-108">擴展內容的實際大小。</span><span class="sxs-lookup"><span data-stu-id="58886-108">[out] The actual size of the context.</span></span> <span data-ttu-id="58886-109">這個值必須小於或等於內容緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="58886-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="58886-110">擴展內容緩衝區。</span><span class="sxs-lookup"><span data-stu-id="58886-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58886-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="58886-111">Return Value</span></span>  

 <span data-ttu-id="58886-112">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="58886-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="58886-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58886-113">HRESULT</span></span>|<span data-ttu-id="58886-114">描述</span><span class="sxs-lookup"><span data-stu-id="58886-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58886-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="58886-115">S_OK</span></span>|<span data-ttu-id="58886-116">已成功傳回目前畫面格的內容。</span><span class="sxs-lookup"><span data-stu-id="58886-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="58886-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58886-117">E_FAIL</span></span>|<span data-ttu-id="58886-118">無法傳回內容。</span><span class="sxs-lookup"><span data-stu-id="58886-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="58886-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT 緩衝區) </span><span class="sxs-lookup"><span data-stu-id="58886-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="58886-120">內容緩衝區太小。</span><span class="sxs-lookup"><span data-stu-id="58886-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="58886-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="58886-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="58886-122">框架指標已在堆疊的結尾;因此，不能存取任何其他框架。</span><span class="sxs-lookup"><span data-stu-id="58886-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="58886-123">例外</span><span class="sxs-lookup"><span data-stu-id="58886-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58886-124">備註</span><span class="sxs-lookup"><span data-stu-id="58886-124">Remarks</span></span>  

 <span data-ttu-id="58886-125">由於回溯只會還原一部分的暫存器，例如非暫時性的暫存器，因此內容可能不會完全符合呼叫時的暫存器狀態。</span><span class="sxs-lookup"><span data-stu-id="58886-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58886-126">需求</span><span class="sxs-lookup"><span data-stu-id="58886-126">Requirements</span></span>  

 <span data-ttu-id="58886-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58886-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58886-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58886-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58886-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58886-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58886-130">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58886-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58886-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58886-131">See also</span></span>

- [<span data-ttu-id="58886-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58886-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="58886-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="58886-133">Debugging</span></span>](index.md)
