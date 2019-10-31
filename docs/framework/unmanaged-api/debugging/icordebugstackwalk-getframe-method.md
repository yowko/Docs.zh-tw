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
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131831"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="f2f27-102">ICorDebugStackWalk::GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="f2f27-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="f2f27-103">取得[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件中的目前框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f27-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2f27-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2f27-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2f27-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="f2f27-106">在建立之框架物件位址的指標，表示堆疊中目前的框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2f27-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2f27-107">Return Value</span></span>  
 <span data-ttu-id="f2f27-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2f27-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f2f27-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2f27-109">HRESULT</span></span>|<span data-ttu-id="f2f27-110">描述</span><span class="sxs-lookup"><span data-stu-id="f2f27-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2f27-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2f27-111">S_OK</span></span>|<span data-ttu-id="f2f27-112">執行時間已成功傳回目前的框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="f2f27-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2f27-113">E_FAIL</span></span>|<span data-ttu-id="f2f27-114">未傳回目前的框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="f2f27-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f2f27-115">S_FALSE</span></span>|<span data-ttu-id="f2f27-116">目前的框架是原生堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="f2f27-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f2f27-117">E_INVALIDARG</span></span>|<span data-ttu-id="f2f27-118">`pFrame` 為 null。</span><span class="sxs-lookup"><span data-stu-id="f2f27-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="f2f27-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f2f27-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="f2f27-120">框架指標已在堆疊的結尾;因此，不能存取任何其他框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f2f27-121">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f2f27-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f27-122">備註</span><span class="sxs-lookup"><span data-stu-id="f2f27-122">Remarks</span></span>  
 <span data-ttu-id="f2f27-123">`ICorDebugStackWalk` 只會傳回實際的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="f2f27-124">請使用[ICorDebugThread3：： GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)方法來傳回內部框架。</span><span class="sxs-lookup"><span data-stu-id="f2f27-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="f2f27-125">（內部畫面是由執行時間推送至堆疊的資料結構，用來儲存暫存資料）。</span><span class="sxs-lookup"><span data-stu-id="f2f27-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f27-126">需求</span><span class="sxs-lookup"><span data-stu-id="f2f27-126">Requirements</span></span>  
 <span data-ttu-id="f2f27-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f27-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f27-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2f27-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2f27-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f27-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f27-130">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f27-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f27-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2f27-131">See also</span></span>

- [<span data-ttu-id="f2f27-132">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="f2f27-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="f2f27-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f2f27-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f2f27-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="f2f27-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
