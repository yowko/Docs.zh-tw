---
title: ICorDebugNativeFrame2::IsMatchingParentFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: aa06b7db6b7371e66853ed242f5e118fb5e5ff0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096193"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="6d3ea-102">ICorDebugNativeFrame2::IsMatchingParentFrame 方法</span><span class="sxs-lookup"><span data-stu-id="6d3ea-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="6d3ea-103">判斷指定的框架是否為目前框架的父系。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d3ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d3ea-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d3ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d3ea-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="6d3ea-106">在您想要針對父狀態評估之框架物件的指標。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="6d3ea-107">[out] `true` 如果 `pPotentialParentFrame` 是目前框架的父系，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d3ea-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6d3ea-108">Return Value</span></span>  
 <span data-ttu-id="6d3ea-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6d3ea-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d3ea-110">HRESULT</span></span>|<span data-ttu-id="6d3ea-111">描述</span><span class="sxs-lookup"><span data-stu-id="6d3ea-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d3ea-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d3ea-112">S_OK</span></span>|<span data-ttu-id="6d3ea-113">父狀態已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="6d3ea-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d3ea-114">E_FAIL</span></span>|<span data-ttu-id="6d3ea-115">無法傳回父系狀態。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="6d3ea-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6d3ea-116">E_INVALIDARG</span></span>|<span data-ttu-id="6d3ea-117">`pPotentialParentFrame` 或 `pIsParent` 為 null。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6d3ea-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="6d3ea-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d3ea-119">備註</span><span class="sxs-lookup"><span data-stu-id="6d3ea-119">Remarks</span></span>  
 <span data-ttu-id="6d3ea-120">如果您傳遞至方法的框架物件是呼叫方法之框架物件的父系，`IsMatchingParentFrame` 會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="6d3ea-121">如果您在不是指定框架之子系的框架上呼叫方法，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d3ea-122">需求</span><span class="sxs-lookup"><span data-stu-id="6d3ea-122">Requirements</span></span>  
 <span data-ttu-id="6d3ea-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d3ea-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d3ea-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d3ea-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d3ea-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d3ea-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d3ea-126">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d3ea-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3ea-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d3ea-127">See also</span></span>

- [<span data-ttu-id="6d3ea-128">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="6d3ea-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="6d3ea-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6d3ea-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6d3ea-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="6d3ea-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
