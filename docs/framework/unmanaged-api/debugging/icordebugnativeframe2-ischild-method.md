---
title: ICorDebugNativeFrame2::IsChild 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9503c12da9e98fbd43f3904aad25c5d10655cec2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075557"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="d4052-102">ICorDebugNativeFrame2::IsChild 方法</span><span class="sxs-lookup"><span data-stu-id="d4052-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="d4052-103">判斷目前的框架是否為子框架。</span><span class="sxs-lookup"><span data-stu-id="d4052-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4052-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4052-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4052-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4052-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="d4052-106">[out]布林值，指定目前的框架是否為子框架。</span><span class="sxs-lookup"><span data-stu-id="d4052-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4052-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4052-107">Return Value</span></span>  
 <span data-ttu-id="d4052-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4052-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d4052-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4052-109">HRESULT</span></span>|<span data-ttu-id="d4052-110">描述</span><span class="sxs-lookup"><span data-stu-id="d4052-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4052-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4052-111">S_OK</span></span>|<span data-ttu-id="d4052-112">已成功地傳回子狀態。</span><span class="sxs-lookup"><span data-stu-id="d4052-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="d4052-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4052-113">E_FAIL</span></span>|<span data-ttu-id="d4052-114">不會傳回子狀態。</span><span class="sxs-lookup"><span data-stu-id="d4052-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="d4052-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d4052-115">E_INVALIDARG</span></span>|`pIsChild` <span data-ttu-id="d4052-116">為 null。</span><span class="sxs-lookup"><span data-stu-id="d4052-116">is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d4052-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d4052-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4052-118">備註</span><span class="sxs-lookup"><span data-stu-id="d4052-118">Remarks</span></span>  
 <span data-ttu-id="d4052-119">`IsChild`方法會傳回`true`框架物件，您可以對其呼叫的方法是否以另一個畫面格的子系。</span><span class="sxs-lookup"><span data-stu-id="d4052-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="d4052-120">如果發生這種情況，使用[IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)方法來檢查其父代是否包含在範圍內。</span><span class="sxs-lookup"><span data-stu-id="d4052-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4052-121">需求</span><span class="sxs-lookup"><span data-stu-id="d4052-121">Requirements</span></span>  
 <span data-ttu-id="d4052-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4052-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4052-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4052-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4052-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4052-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d4052-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d4052-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4052-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4052-126">See also</span></span>

- [<span data-ttu-id="d4052-127">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="d4052-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="d4052-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d4052-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d4052-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="d4052-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
