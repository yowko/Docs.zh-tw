---
title: "ICorDebugThread3::GetActiveInternalFrames 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ecfbaeff9416ee8e6541a23bac6ec76f99abd2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="663be-102">ICorDebugThread3::GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="663be-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="663be-103">傳回內部框架的陣列 ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)物件) 堆疊上。</span><span class="sxs-lookup"><span data-stu-id="663be-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="663be-104">語法</span><span class="sxs-lookup"><span data-stu-id="663be-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="663be-105">參數</span><span class="sxs-lookup"><span data-stu-id="663be-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="663be-106">[in]中必須要有內部的畫面格數目`ppInternalFrames`。</span><span class="sxs-lookup"><span data-stu-id="663be-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="663be-107">[out]指標`ULONG32`，其中包含內部堆疊上框架的數目。</span><span class="sxs-lookup"><span data-stu-id="663be-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="663be-108">[in、 out]陣列內部堆疊上框架的位址指標。</span><span class="sxs-lookup"><span data-stu-id="663be-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="663be-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="663be-109">Return Value</span></span>  
 <span data-ttu-id="663be-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="663be-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="663be-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="663be-111">HRESULT</span></span>|<span data-ttu-id="663be-112">描述</span><span class="sxs-lookup"><span data-stu-id="663be-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="663be-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="663be-113">S_OK</span></span>|<span data-ttu-id="663be-114">[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)物件已建立成功。</span><span class="sxs-lookup"><span data-stu-id="663be-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="663be-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="663be-115">E_INVALIDARG</span></span>|<span data-ttu-id="663be-116">`cInternalFrames`不是零和`ppInternalFrames`是`null`，或`pcInternalFrames`是`null`。</span><span class="sxs-lookup"><span data-stu-id="663be-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="663be-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="663be-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="663be-118">`ppInternalFrames`小於內部框架的計數。</span><span class="sxs-lookup"><span data-stu-id="663be-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="663be-119">例外狀況</span><span class="sxs-lookup"><span data-stu-id="663be-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="663be-120">備註</span><span class="sxs-lookup"><span data-stu-id="663be-120">Remarks</span></span>  
 <span data-ttu-id="663be-121">內部框架是一種資料結構來儲存暫存資料推送到堆疊上由執行階段。</span><span class="sxs-lookup"><span data-stu-id="663be-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="663be-122">當您第一次呼叫`GetActiveInternalFrames`，您應該設定`cInternalFrames`參數為 0 （零），而`ppInternalFrames`參數為 null。</span><span class="sxs-lookup"><span data-stu-id="663be-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="663be-123">當`GetActiveInternalFrames`會先傳回，`pcInternalFrames`包含內部堆疊上框架的計數。</span><span class="sxs-lookup"><span data-stu-id="663be-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="663be-124">`GetActiveInternalFrames`應該接著呼叫第二次。</span><span class="sxs-lookup"><span data-stu-id="663be-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="663be-125">您應該傳遞正確的計數 (`pcInternalFrames`) 中`cInternalFrames`參數，並指定適當大小的陣列中的指標`ppInternalFrames`。</span><span class="sxs-lookup"><span data-stu-id="663be-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="663be-126">使用[icordebugstackwalk:: Getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)方法以傳回實際堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="663be-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="663be-127">需求</span><span class="sxs-lookup"><span data-stu-id="663be-127">Requirements</span></span>  
 <span data-ttu-id="663be-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="663be-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="663be-129">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="663be-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="663be-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="663be-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="663be-131">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="663be-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663be-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="663be-132">See Also</span></span>  
 [<span data-ttu-id="663be-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="663be-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="663be-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="663be-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
