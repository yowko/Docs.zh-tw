---
title: "ICorDebugNativeFrame2::IsMatchingParentFrame 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc2d8eacb05e861290ad19a34c261943dc2959a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="7f977-102">ICorDebugNativeFrame2::IsMatchingParentFrame 方法</span><span class="sxs-lookup"><span data-stu-id="7f977-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="7f977-103">判斷指定的範圍是否為目前的畫面格的父代。</span><span class="sxs-lookup"><span data-stu-id="7f977-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f977-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f977-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f977-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f977-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="7f977-106">[in]您想要評估父狀態框架物件的指標。</span><span class="sxs-lookup"><span data-stu-id="7f977-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="7f977-107">[out]`true`如果`pPotentialParentFrame`是目前畫面格的父代，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="7f977-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f977-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7f977-108">Return Value</span></span>  
 <span data-ttu-id="7f977-109">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f977-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7f977-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f977-110">HRESULT</span></span>|<span data-ttu-id="7f977-111">描述</span><span class="sxs-lookup"><span data-stu-id="7f977-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f977-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f977-112">S_OK</span></span>|<span data-ttu-id="7f977-113">已成功地傳回父狀態。</span><span class="sxs-lookup"><span data-stu-id="7f977-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="7f977-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f977-114">E_FAIL</span></span>|<span data-ttu-id="7f977-115">不會傳回父狀態。</span><span class="sxs-lookup"><span data-stu-id="7f977-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="7f977-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7f977-116">E_INVALIDARG</span></span>|<span data-ttu-id="7f977-117">`pPotentialParentFrame` 或 `pIsParent` 為 null。</span><span class="sxs-lookup"><span data-stu-id="7f977-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="7f977-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7f977-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f977-119">備註</span><span class="sxs-lookup"><span data-stu-id="7f977-119">Remarks</span></span>  
 <span data-ttu-id="7f977-120">`IsMatchingParentFrame`傳回`true`框架物件傳遞至該方法是否呼叫此方法的框架物件的父系。</span><span class="sxs-lookup"><span data-stu-id="7f977-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="7f977-121">如果您不是子系為指定框架的框架上呼叫方法，它會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f977-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f977-122">需求</span><span class="sxs-lookup"><span data-stu-id="7f977-122">Requirements</span></span>  
 <span data-ttu-id="7f977-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f977-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f977-124">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f977-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f977-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f977-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f977-126">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f977-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f977-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f977-127">See Also</span></span>  
 [<span data-ttu-id="7f977-128">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="7f977-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="7f977-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7f977-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7f977-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="7f977-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
