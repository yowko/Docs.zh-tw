---
title: ICorDebugThread3::GetActiveInternalFrames 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178458"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="6999b-102">ICorDebugThread3::GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="6999b-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="6999b-103">返回堆疊上的內部幀陣列[（ICorDebug內部Frame2](icordebuginternalframe2-interface.md)物件）。</span><span class="sxs-lookup"><span data-stu-id="6999b-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6999b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6999b-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6999b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6999b-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="6999b-106">[在]中預期的內部幀數`ppInternalFrames`。</span><span class="sxs-lookup"><span data-stu-id="6999b-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="6999b-107">[出]指向`ULONG32`包含堆疊上內部幀數的 指標。</span><span class="sxs-lookup"><span data-stu-id="6999b-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="6999b-108">[進出]指向堆疊上內部幀陣列位址的指標。</span><span class="sxs-lookup"><span data-stu-id="6999b-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6999b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6999b-109">Return Value</span></span>  
 <span data-ttu-id="6999b-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6999b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6999b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6999b-111">HRESULT</span></span>|<span data-ttu-id="6999b-112">描述</span><span class="sxs-lookup"><span data-stu-id="6999b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6999b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6999b-113">S_OK</span></span>|<span data-ttu-id="6999b-114">已成功創建[ICorDebug 內部Frame2](icordebuginternalframe2-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="6999b-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="6999b-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6999b-115">E_INVALIDARG</span></span>|<span data-ttu-id="6999b-116">`cInternalFrames``ppInternalFrames`不是零，`null`是 ，`pcInternalFrames`或`null`是 。</span><span class="sxs-lookup"><span data-stu-id="6999b-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="6999b-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="6999b-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="6999b-118">`ppInternalFrames`小於內部幀的計數。</span><span class="sxs-lookup"><span data-stu-id="6999b-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6999b-119">例外狀況</span><span class="sxs-lookup"><span data-stu-id="6999b-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6999b-120">備註</span><span class="sxs-lookup"><span data-stu-id="6999b-120">Remarks</span></span>  
 <span data-ttu-id="6999b-121">內部幀是運行時推送到堆疊以存儲臨時資料的資料結構。</span><span class="sxs-lookup"><span data-stu-id="6999b-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="6999b-122">首次調用`GetActiveInternalFrames`時，應將`cInternalFrames`參數設置為 0（零），並將`ppInternalFrames`參數設置為 null。</span><span class="sxs-lookup"><span data-stu-id="6999b-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="6999b-123">首次`GetActiveInternalFrames`返回時，`pcInternalFrames`包含堆疊上內部幀的計數。</span><span class="sxs-lookup"><span data-stu-id="6999b-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="6999b-124">`GetActiveInternalFrames`然後，應調用第二次。</span><span class="sxs-lookup"><span data-stu-id="6999b-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="6999b-125">應在`pcInternalFrames``cInternalFrames`參數中傳遞正確的計數 （ ），並在 中指定指向適當大小的陣列的`ppInternalFrames`指標。</span><span class="sxs-lookup"><span data-stu-id="6999b-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="6999b-126">使用[ICorDebugStackWalk：getFrame](icordebugthread3-getactiveinternalframes-method.md)方法返回實際堆疊幀。</span><span class="sxs-lookup"><span data-stu-id="6999b-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6999b-127">需求</span><span class="sxs-lookup"><span data-stu-id="6999b-127">Requirements</span></span>  
 <span data-ttu-id="6999b-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6999b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6999b-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6999b-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6999b-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6999b-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6999b-131">**.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6999b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6999b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6999b-132">See also</span></span>

- [<span data-ttu-id="6999b-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6999b-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6999b-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="6999b-134">Debugging</span></span>](index.md)
