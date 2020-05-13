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
ms.openlocfilehash: 759ba7bd46f8231143e743aa5ffcabffeb99c3b6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205103"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="d35a5-102">ICorDebugNativeFrame2::IsChild 方法</span><span class="sxs-lookup"><span data-stu-id="d35a5-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="d35a5-103">判斷目前的框架是否為子框架。</span><span class="sxs-lookup"><span data-stu-id="d35a5-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="d35a5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d35a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="d35a5-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="d35a5-106">脫銷布林值，指定目前的框架是否為子框架。</span><span class="sxs-lookup"><span data-stu-id="d35a5-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d35a5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d35a5-107">Return Value</span></span>  
 <span data-ttu-id="d35a5-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d35a5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d35a5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d35a5-109">HRESULT</span></span>|<span data-ttu-id="d35a5-110">描述</span><span class="sxs-lookup"><span data-stu-id="d35a5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d35a5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d35a5-111">S_OK</span></span>|<span data-ttu-id="d35a5-112">已成功傳回子系狀態。</span><span class="sxs-lookup"><span data-stu-id="d35a5-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="d35a5-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d35a5-113">E_FAIL</span></span>|<span data-ttu-id="d35a5-114">無法傳回子狀態。</span><span class="sxs-lookup"><span data-stu-id="d35a5-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="d35a5-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d35a5-115">E_INVALIDARG</span></span>|<span data-ttu-id="d35a5-116">`pIsChild` 為 null。</span><span class="sxs-lookup"><span data-stu-id="d35a5-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d35a5-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d35a5-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d35a5-118">備註</span><span class="sxs-lookup"><span data-stu-id="d35a5-118">Remarks</span></span>  
 <span data-ttu-id="d35a5-119">`IsChild` `true` 如果您呼叫方法的框架物件是另一個框架的子系，則此方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="d35a5-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="d35a5-120">如果是這種情況，請使用[IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md)方法來檢查框架是否為其父系。</span><span class="sxs-lookup"><span data-stu-id="d35a5-120">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35a5-121">需求</span><span class="sxs-lookup"><span data-stu-id="d35a5-121">Requirements</span></span>  
 <span data-ttu-id="d35a5-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d35a5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35a5-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d35a5-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d35a5-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d35a5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d35a5-125">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35a5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35a5-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="d35a5-126">See also</span></span>

- [<span data-ttu-id="d35a5-127">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="d35a5-127">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="d35a5-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d35a5-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d35a5-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="d35a5-129">Debugging</span></span>](index.md)
