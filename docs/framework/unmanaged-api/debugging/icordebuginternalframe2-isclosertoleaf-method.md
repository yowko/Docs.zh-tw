---
title: "ICorDebugInternalFrame2::IsCloserToLeaf 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60e63800ade5fb0d4a222d80ebfe43c3d84c2815
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="81e8a-102">ICorDebugInternalFrame2::IsCloserToLeaf 方法</span><span class="sxs-lookup"><span data-stu-id="81e8a-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="81e8a-103">檢查是否`this`內部框架為愈接近分葉與指定的 ICorDebugFrame 物件。</span><span class="sxs-lookup"><span data-stu-id="81e8a-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="81e8a-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81e8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="81e8a-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="81e8a-106">[in]比較指標`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="81e8a-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="81e8a-107">[out]`true`如果`this`內部框架比較接近於所指定的框架的分葉`pFrameToCompare`，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="81e8a-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81e8a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="81e8a-108">Return Value</span></span>  
 <span data-ttu-id="81e8a-109">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="81e8a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="81e8a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81e8a-110">HRESULT</span></span>|<span data-ttu-id="81e8a-111">描述</span><span class="sxs-lookup"><span data-stu-id="81e8a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81e8a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="81e8a-112">S_OK</span></span>|<span data-ttu-id="81e8a-113">已成功執行比較。</span><span class="sxs-lookup"><span data-stu-id="81e8a-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="81e8a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81e8a-114">E_FAIL</span></span>|<span data-ttu-id="81e8a-115">無法執行比較。</span><span class="sxs-lookup"><span data-stu-id="81e8a-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="81e8a-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="81e8a-116">E_INVALIDARG</span></span>|<span data-ttu-id="81e8a-117">`pFrameToCompare` 或 `pIsCloser` 為 null。</span><span class="sxs-lookup"><span data-stu-id="81e8a-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e8a-118">備註</span><span class="sxs-lookup"><span data-stu-id="81e8a-118">Remarks</span></span>  
 <span data-ttu-id="81e8a-119">`IsCloserToLeaf`可用來實作交錯內部與其他框架的堆疊上框架的原則。</span><span class="sxs-lookup"><span data-stu-id="81e8a-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e8a-120">需求</span><span class="sxs-lookup"><span data-stu-id="81e8a-120">Requirements</span></span>  
 <span data-ttu-id="81e8a-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81e8a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e8a-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81e8a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81e8a-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81e8a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81e8a-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e8a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e8a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e8a-125">See Also</span></span>  
 [<span data-ttu-id="81e8a-126">ICorDebugInternalFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="81e8a-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="81e8a-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="81e8a-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="81e8a-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="81e8a-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
