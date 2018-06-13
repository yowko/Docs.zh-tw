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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 548a8a7743c02be5734b677010627f847c5bc4b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421983"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="47145-102">ICorDebugStackWalk::GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="47145-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="47145-103">取得目前的框架中[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="47145-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47145-104">語法</span><span class="sxs-lookup"><span data-stu-id="47145-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47145-105">參數</span><span class="sxs-lookup"><span data-stu-id="47145-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="47145-106">[in]建立的框架物件，代表目前的堆疊框架的位址指標。</span><span class="sxs-lookup"><span data-stu-id="47145-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47145-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="47145-107">Return Value</span></span>  
 <span data-ttu-id="47145-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="47145-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47145-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47145-109">HRESULT</span></span>|<span data-ttu-id="47145-110">描述</span><span class="sxs-lookup"><span data-stu-id="47145-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47145-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="47145-111">S_OK</span></span>|<span data-ttu-id="47145-112">執行階段成功地傳回目前的框架。</span><span class="sxs-lookup"><span data-stu-id="47145-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="47145-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47145-113">E_FAIL</span></span>|<span data-ttu-id="47145-114">未傳回目前的框架。</span><span class="sxs-lookup"><span data-stu-id="47145-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="47145-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="47145-115">S_FALSE</span></span>|<span data-ttu-id="47145-116">目前的框架是原生堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="47145-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="47145-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="47145-117">E_INVALIDARG</span></span>|<span data-ttu-id="47145-118">`pFrame` 為 null。</span><span class="sxs-lookup"><span data-stu-id="47145-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="47145-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="47145-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="47145-120">框架指標已經結尾的堆疊。因此，沒有其他框架則可以存取。</span><span class="sxs-lookup"><span data-stu-id="47145-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="47145-121">例外狀況</span><span class="sxs-lookup"><span data-stu-id="47145-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47145-122">備註</span><span class="sxs-lookup"><span data-stu-id="47145-122">Remarks</span></span>  
 <span data-ttu-id="47145-123">`ICorDebugStackWalk` 傳回只有實際的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="47145-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="47145-124">使用[icordebugthread3:: Getactiveinternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)方法來傳回內部框架。</span><span class="sxs-lookup"><span data-stu-id="47145-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="47145-125">（內部框架是資料結構來儲存暫存資料推送到堆疊上由執行階段）。</span><span class="sxs-lookup"><span data-stu-id="47145-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47145-126">需求</span><span class="sxs-lookup"><span data-stu-id="47145-126">Requirements</span></span>  
 <span data-ttu-id="47145-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47145-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47145-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47145-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47145-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47145-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47145-130">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47145-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47145-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47145-131">See Also</span></span>  
 [<span data-ttu-id="47145-132">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="47145-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="47145-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="47145-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="47145-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="47145-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
