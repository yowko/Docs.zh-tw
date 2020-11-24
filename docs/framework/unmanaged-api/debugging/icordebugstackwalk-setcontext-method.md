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
ms.openlocfilehash: 1ae9fc1f1154866945d40cd63042fa8a43b88905
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677293"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="c3fed-102">ICorDebugStackWalk::SetContext 方法</span><span class="sxs-lookup"><span data-stu-id="c3fed-102">ICorDebugStackWalk::SetContext Method</span></span>

<span data-ttu-id="c3fed-103">將 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 物件的目前內容設定為執行緒的有效內容。</span><span class="sxs-lookup"><span data-stu-id="c3fed-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3fed-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3fed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3fed-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3fed-105">Parameters</span></span>  

 `flag`  
 <span data-ttu-id="c3fed-106">在 [CorDebugSetCoNtextFlag](cordebugsetcontextflag-enumeration.md) 旗標，指出內容是否來自堆疊上的作用中框架，或回溯堆疊所取得的內容。</span><span class="sxs-lookup"><span data-stu-id="c3fed-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c3fed-107">在緩衝區的配置大小 `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="c3fed-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="c3fed-108">在 `CONTEXT` 緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c3fed-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3fed-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c3fed-109">Return Value</span></span>  

 <span data-ttu-id="c3fed-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3fed-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c3fed-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3fed-111">HRESULT</span></span>|<span data-ttu-id="c3fed-112">描述</span><span class="sxs-lookup"><span data-stu-id="c3fed-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3fed-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3fed-113">S_OK</span></span>|<span data-ttu-id="c3fed-114">已 `ICorDebugStackWalk` 成功設定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="c3fed-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="c3fed-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3fed-115">E_FAIL</span></span>|<span data-ttu-id="c3fed-116">`ICorDebugStackWalk`未設定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="c3fed-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="c3fed-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c3fed-117">E_INVALIDARG</span></span>|<span data-ttu-id="c3fed-118">內容為 null。</span><span class="sxs-lookup"><span data-stu-id="c3fed-118">The context is null.</span></span>|  
|<span data-ttu-id="c3fed-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="c3fed-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="c3fed-120">內容緩衝區太小。</span><span class="sxs-lookup"><span data-stu-id="c3fed-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c3fed-121">例外</span><span class="sxs-lookup"><span data-stu-id="c3fed-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3fed-122">備註</span><span class="sxs-lookup"><span data-stu-id="c3fed-122">Remarks</span></span>  

 <span data-ttu-id="c3fed-123">這個方法不會改變執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="c3fed-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="c3fed-124">將目前的內容設定為不正確內容，可能會導致堆疊遍歷程式無法預期的結果。</span><span class="sxs-lookup"><span data-stu-id="c3fed-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="c3fed-125">您可以立即呼叫 [ICorDebugStackWalk：： GetCoNtext](icordebugstackwalk-getcontext-method.md) 方法，以取得此內容的精確位複製。</span><span class="sxs-lookup"><span data-stu-id="c3fed-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3fed-126">需求</span><span class="sxs-lookup"><span data-stu-id="c3fed-126">Requirements</span></span>  

 <span data-ttu-id="c3fed-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3fed-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3fed-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3fed-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3fed-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3fed-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3fed-130">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3fed-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fed-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3fed-131">See also</span></span>

- [<span data-ttu-id="c3fed-132">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c3fed-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c3fed-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="c3fed-133">Debugging</span></span>](index.md)
