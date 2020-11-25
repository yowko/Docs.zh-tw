---
title: ICorDebugStackWalk::GetFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 452635764794e01858baab10464a03c966a55271
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711932"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="e3230-102">ICorDebugStackWalk::GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="e3230-102">ICorDebugStackWalk::GetFrame Method</span></span>

<span data-ttu-id="e3230-103">取得 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 物件中目前的框架。</span><span class="sxs-lookup"><span data-stu-id="e3230-103">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3230-104">語法</span><span class="sxs-lookup"><span data-stu-id="e3230-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3230-105">參數</span><span class="sxs-lookup"><span data-stu-id="e3230-105">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="e3230-106">在所建立框架物件位址的指標，代表堆疊中目前的框架。</span><span class="sxs-lookup"><span data-stu-id="e3230-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3230-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e3230-107">Return Value</span></span>  

 <span data-ttu-id="e3230-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3230-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e3230-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3230-109">HRESULT</span></span>|<span data-ttu-id="e3230-110">描述</span><span class="sxs-lookup"><span data-stu-id="e3230-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3230-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3230-111">S_OK</span></span>|<span data-ttu-id="e3230-112">執行時間成功傳回目前的框架。</span><span class="sxs-lookup"><span data-stu-id="e3230-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="e3230-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3230-113">E_FAIL</span></span>|<span data-ttu-id="e3230-114">未傳回目前的畫面格。</span><span class="sxs-lookup"><span data-stu-id="e3230-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="e3230-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e3230-115">S_FALSE</span></span>|<span data-ttu-id="e3230-116">目前的畫面格是原生堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="e3230-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="e3230-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e3230-117">E_INVALIDARG</span></span>|<span data-ttu-id="e3230-118">`pFrame` 為 null。</span><span class="sxs-lookup"><span data-stu-id="e3230-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="e3230-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="e3230-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="e3230-120">框架指標已在堆疊的結尾;因此，不能存取任何其他框架。</span><span class="sxs-lookup"><span data-stu-id="e3230-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e3230-121">例外</span><span class="sxs-lookup"><span data-stu-id="e3230-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3230-122">備註</span><span class="sxs-lookup"><span data-stu-id="e3230-122">Remarks</span></span>  

 <span data-ttu-id="e3230-123">`ICorDebugStackWalk` 只傳回實際的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="e3230-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="e3230-124">使用 [ICorDebugThread3：： GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) 方法來傳回內部畫面格。</span><span class="sxs-lookup"><span data-stu-id="e3230-124">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="e3230-125"> (內部畫面是由執行時間推送至堆疊的資料結構，用來儲存暫存資料。 ) </span><span class="sxs-lookup"><span data-stu-id="e3230-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3230-126">需求</span><span class="sxs-lookup"><span data-stu-id="e3230-126">Requirements</span></span>  

 <span data-ttu-id="e3230-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3230-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3230-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3230-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3230-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3230-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3230-130">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3230-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3230-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3230-131">See also</span></span>

- [<span data-ttu-id="e3230-132">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="e3230-132">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="e3230-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e3230-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e3230-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="e3230-134">Debugging</span></span>](index.md)
