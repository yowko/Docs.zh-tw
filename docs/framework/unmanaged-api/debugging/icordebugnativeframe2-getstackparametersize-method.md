---
title: "ICorDebugNativeFrame2::GetStackParameterSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c265cb564718b362b1354189e59dc217b2866b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="4681d-102">ICorDebugNativeFrame2::GetStackParameterSize 方法</span><span class="sxs-lookup"><span data-stu-id="4681d-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="4681d-103">在 x86 作業系統上的堆疊上傳回參數的累計大小。</span><span class="sxs-lookup"><span data-stu-id="4681d-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4681d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4681d-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4681d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4681d-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="4681d-106">[out]在堆疊上的參數累計大小的指標。</span><span class="sxs-lookup"><span data-stu-id="4681d-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4681d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4681d-107">Return Value</span></span>  
 <span data-ttu-id="4681d-108">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="4681d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4681d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4681d-109">HRESULT</span></span>|<span data-ttu-id="4681d-110">描述</span><span class="sxs-lookup"><span data-stu-id="4681d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4681d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4681d-111">S_OK</span></span>|<span data-ttu-id="4681d-112">已成功地傳回堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="4681d-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="4681d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4681d-113">S_FALSE</span></span>|<span data-ttu-id="4681d-114">`GetStackParameterSize`在非 x86 平台上呼叫。</span><span class="sxs-lookup"><span data-stu-id="4681d-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="4681d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4681d-115">E_FAIL</span></span>|<span data-ttu-id="4681d-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="4681d-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="4681d-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4681d-117">E_INVALIDARG</span></span>|<span data-ttu-id="4681d-118">`pSize`是`null`。</span><span class="sxs-lookup"><span data-stu-id="4681d-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4681d-119">例外狀況</span><span class="sxs-lookup"><span data-stu-id="4681d-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4681d-120">備註</span><span class="sxs-lookup"><span data-stu-id="4681d-120">Remarks</span></span>  
 <span data-ttu-id="4681d-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)方法不會調整參數，推入堆疊的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="4681d-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="4681d-122">相反地，您可以使用所傳回的值`GetStackParameterSize`調整來植入原生回溯器，並調整參數的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="4681d-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4681d-123">需求</span><span class="sxs-lookup"><span data-stu-id="4681d-123">Requirements</span></span>  
 <span data-ttu-id="4681d-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4681d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4681d-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4681d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4681d-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4681d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4681d-127">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4681d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4681d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4681d-128">See Also</span></span>  
 [<span data-ttu-id="4681d-129">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="4681d-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="4681d-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4681d-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4681d-131">偵錯</span><span class="sxs-lookup"><span data-stu-id="4681d-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
