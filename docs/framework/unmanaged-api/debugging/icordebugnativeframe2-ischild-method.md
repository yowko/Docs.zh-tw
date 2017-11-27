---
title: "ICorDebugNativeFrame2::IsChild 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsChild Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 006543e473ca3b7cc1818b2b4641567ce37f6f0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="bc0f7-102">ICorDebugNativeFrame2::IsChild 方法</span><span class="sxs-lookup"><span data-stu-id="bc0f7-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="bc0f7-103">判斷目前的框架是子框架。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc0f7-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc0f7-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc0f7-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="bc0f7-106">[out]布林值，指定目前的框架是否為子框架。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc0f7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc0f7-107">Return Value</span></span>  
 <span data-ttu-id="bc0f7-108">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bc0f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc0f7-109">HRESULT</span></span>|<span data-ttu-id="bc0f7-110">描述</span><span class="sxs-lookup"><span data-stu-id="bc0f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc0f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc0f7-111">S_OK</span></span>|<span data-ttu-id="bc0f7-112">已成功傳回的子狀態。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="bc0f7-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc0f7-113">E_FAIL</span></span>|<span data-ttu-id="bc0f7-114">不會傳回子狀態。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="bc0f7-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bc0f7-115">E_INVALIDARG</span></span>|<span data-ttu-id="bc0f7-116">`pIsChild` 為 null。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bc0f7-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="bc0f7-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc0f7-118">備註</span><span class="sxs-lookup"><span data-stu-id="bc0f7-118">Remarks</span></span>  
 <span data-ttu-id="bc0f7-119">`IsChild`方法會傳回`true`框架物件呼叫方法是否另一個畫面格的子系。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="bc0f7-120">如果這種情況，使用[IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)方法來檢查是否在範圍內為其父系。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0f7-121">需求</span><span class="sxs-lookup"><span data-stu-id="bc0f7-121">Requirements</span></span>  
 <span data-ttu-id="bc0f7-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc0f7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0f7-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc0f7-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc0f7-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc0f7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc0f7-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0f7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0f7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc0f7-126">See Also</span></span>  
 [<span data-ttu-id="bc0f7-127">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="bc0f7-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="bc0f7-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bc0f7-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bc0f7-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="bc0f7-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
