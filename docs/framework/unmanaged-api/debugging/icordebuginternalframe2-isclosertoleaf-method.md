---
title: ICorDebugInternalFrame2::IsCloserToLeaf 方法
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96deee943f6a4c636a52b41c8f4c2fda86c6bd18
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493715"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="38c7c-102">ICorDebugInternalFrame2::IsCloserToLeaf 方法</span><span class="sxs-lookup"><span data-stu-id="38c7c-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="38c7c-103">檢查是否`this`內部框架是接近 ICorDebugFrame 物件和指定的分葉。</span><span class="sxs-lookup"><span data-stu-id="38c7c-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="38c7c-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38c7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="38c7c-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="38c7c-106">[in]比較指標`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="38c7c-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="38c7c-107">[out]`true`如果`this`內部框架是所指定的框架比接近分葉`pFrameToCompare`; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="38c7c-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38c7c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="38c7c-108">Return Value</span></span>  
 <span data-ttu-id="38c7c-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="38c7c-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="38c7c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38c7c-110">HRESULT</span></span>|<span data-ttu-id="38c7c-111">描述</span><span class="sxs-lookup"><span data-stu-id="38c7c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38c7c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="38c7c-112">S_OK</span></span>|<span data-ttu-id="38c7c-113">已成功進行比較。</span><span class="sxs-lookup"><span data-stu-id="38c7c-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="38c7c-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38c7c-114">E_FAIL</span></span>|<span data-ttu-id="38c7c-115">無法執行比較。</span><span class="sxs-lookup"><span data-stu-id="38c7c-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="38c7c-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="38c7c-116">E_INVALIDARG</span></span>|<span data-ttu-id="38c7c-117">`pFrameToCompare` 或`pIsCloser`為 null。</span><span class="sxs-lookup"><span data-stu-id="38c7c-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38c7c-118">備註</span><span class="sxs-lookup"><span data-stu-id="38c7c-118">Remarks</span></span>  
 <span data-ttu-id="38c7c-119">`IsCloserToLeaf` 可用來實作交錯內部框架具有其他框架在堆疊上的原則。</span><span class="sxs-lookup"><span data-stu-id="38c7c-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38c7c-120">需求</span><span class="sxs-lookup"><span data-stu-id="38c7c-120">Requirements</span></span>  
 <span data-ttu-id="38c7c-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38c7c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38c7c-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38c7c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38c7c-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38c7c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38c7c-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38c7c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c7c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38c7c-125">See also</span></span>
- [<span data-ttu-id="38c7c-126">ICorDebugInternalFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="38c7c-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="38c7c-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="38c7c-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="38c7c-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="38c7c-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
