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
ms.openlocfilehash: 2ca3bf94298b45e404c930ffe52e101085ee482d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726206"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="b48e7-102">ICorDebugThread3::GetActiveInternalFrames 方法</span><span class="sxs-lookup"><span data-stu-id="b48e7-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>

<span data-ttu-id="b48e7-103">傳回內部框架的陣列， (堆疊上) 的 [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="b48e7-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b48e7-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b48e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b48e7-105">Parameters</span></span>  

 `cInternalFrames`  
 <span data-ttu-id="b48e7-106">在預期的內部框架數目 `ppInternalFrames` 。</span><span class="sxs-lookup"><span data-stu-id="b48e7-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="b48e7-107">擴展的指標 `ULONG32` ，其中包含堆疊上的內部框架數目。</span><span class="sxs-lookup"><span data-stu-id="b48e7-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="b48e7-108">[in，out]堆疊上內部框架陣列的位址指標。</span><span class="sxs-lookup"><span data-stu-id="b48e7-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b48e7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b48e7-109">Return Value</span></span>  

 <span data-ttu-id="b48e7-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="b48e7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b48e7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b48e7-111">HRESULT</span></span>|<span data-ttu-id="b48e7-112">描述</span><span class="sxs-lookup"><span data-stu-id="b48e7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b48e7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b48e7-113">S_OK</span></span>|<span data-ttu-id="b48e7-114">已成功建立 [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="b48e7-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="b48e7-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b48e7-115">E_INVALIDARG</span></span>|<span data-ttu-id="b48e7-116">`cInternalFrames` 不是零，而且 `ppInternalFrames` 是 `null` ， `pcInternalFrames` 或是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="b48e7-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="b48e7-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="b48e7-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="b48e7-118">`ppInternalFrames` 小於內部框架的計數。</span><span class="sxs-lookup"><span data-stu-id="b48e7-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b48e7-119">例外</span><span class="sxs-lookup"><span data-stu-id="b48e7-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b48e7-120">備註</span><span class="sxs-lookup"><span data-stu-id="b48e7-120">Remarks</span></span>  

 <span data-ttu-id="b48e7-121">內部畫面是由執行時間推送至堆疊的資料結構，用來儲存暫存資料。</span><span class="sxs-lookup"><span data-stu-id="b48e7-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="b48e7-122">當您第一次呼叫時 `GetActiveInternalFrames` ，您應該將 `cInternalFrames` 參數設定為 0 (零) ，並將參數設定為 `ppInternalFrames` null。</span><span class="sxs-lookup"><span data-stu-id="b48e7-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="b48e7-123">`GetActiveInternalFrames`第一次傳回時， `pcInternalFrames` 包含堆疊上的內部框架計數。</span><span class="sxs-lookup"><span data-stu-id="b48e7-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="b48e7-124">`GetActiveInternalFrames` 然後再呼叫第二次。</span><span class="sxs-lookup"><span data-stu-id="b48e7-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="b48e7-125">您應該在參數中傳遞適當的計數 (`pcInternalFrames`) `cInternalFrames` ，並在中指定適當大小的陣列指標 `ppInternalFrames` 。</span><span class="sxs-lookup"><span data-stu-id="b48e7-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="b48e7-126">使用 [ICorDebugStackWalk：： GetFrame](icordebugthread3-getactiveinternalframes-method.md) 方法來傳回實際的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="b48e7-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b48e7-127">需求</span><span class="sxs-lookup"><span data-stu-id="b48e7-127">Requirements</span></span>  

 <span data-ttu-id="b48e7-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b48e7-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b48e7-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b48e7-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b48e7-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b48e7-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b48e7-131">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b48e7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48e7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b48e7-132">See also</span></span>

- [<span data-ttu-id="b48e7-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b48e7-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b48e7-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="b48e7-134">Debugging</span></span>](index.md)
