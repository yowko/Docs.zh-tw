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
ms.workload: dotnet
ms.openlocfilehash: 267bc2fcd03786bfceb218dd0218ffa7006f8fa7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="49207-102">ICorDebugNativeFrame2::IsChild 方法</span><span class="sxs-lookup"><span data-stu-id="49207-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="49207-103">判斷目前的框架是子框架。</span><span class="sxs-lookup"><span data-stu-id="49207-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49207-104">語法</span><span class="sxs-lookup"><span data-stu-id="49207-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49207-105">參數</span><span class="sxs-lookup"><span data-stu-id="49207-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="49207-106">[out]布林值，指定目前的框架是否為子框架。</span><span class="sxs-lookup"><span data-stu-id="49207-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49207-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="49207-107">Return Value</span></span>  
 <span data-ttu-id="49207-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="49207-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="49207-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49207-109">HRESULT</span></span>|<span data-ttu-id="49207-110">描述</span><span class="sxs-lookup"><span data-stu-id="49207-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49207-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="49207-111">S_OK</span></span>|<span data-ttu-id="49207-112">已成功傳回的子狀態。</span><span class="sxs-lookup"><span data-stu-id="49207-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="49207-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49207-113">E_FAIL</span></span>|<span data-ttu-id="49207-114">不會傳回子狀態。</span><span class="sxs-lookup"><span data-stu-id="49207-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="49207-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="49207-115">E_INVALIDARG</span></span>|<span data-ttu-id="49207-116">`pIsChild` 為 null。</span><span class="sxs-lookup"><span data-stu-id="49207-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="49207-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="49207-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49207-118">備註</span><span class="sxs-lookup"><span data-stu-id="49207-118">Remarks</span></span>  
 <span data-ttu-id="49207-119">`IsChild`方法會傳回`true`框架物件呼叫方法是否另一個畫面格的子系。</span><span class="sxs-lookup"><span data-stu-id="49207-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="49207-120">如果這種情況，使用[IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)方法來檢查是否在範圍內為其父系。</span><span class="sxs-lookup"><span data-stu-id="49207-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49207-121">需求</span><span class="sxs-lookup"><span data-stu-id="49207-121">Requirements</span></span>  
 <span data-ttu-id="49207-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49207-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49207-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49207-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49207-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49207-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49207-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49207-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49207-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="49207-126">See Also</span></span>  
 [<span data-ttu-id="49207-127">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="49207-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="49207-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="49207-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="49207-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="49207-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
