---
title: "ICorDebugNativeFrame2::GetStackParameterSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa7e67c252f2ece16c072e22d0333e085fbc4f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="7a589-102">ICorDebugNativeFrame2::GetStackParameterSize 方法</span><span class="sxs-lookup"><span data-stu-id="7a589-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="7a589-103">在 x86 作業系統上的堆疊上傳回參數的累計大小。</span><span class="sxs-lookup"><span data-stu-id="7a589-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a589-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a589-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a589-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a589-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="7a589-106">[out]在堆疊上的參數累計大小的指標。</span><span class="sxs-lookup"><span data-stu-id="7a589-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a589-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7a589-107">Return Value</span></span>  
 <span data-ttu-id="7a589-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7a589-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7a589-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a589-109">HRESULT</span></span>|<span data-ttu-id="7a589-110">描述</span><span class="sxs-lookup"><span data-stu-id="7a589-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a589-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a589-111">S_OK</span></span>|<span data-ttu-id="7a589-112">已成功地傳回堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="7a589-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="7a589-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7a589-113">S_FALSE</span></span>|<span data-ttu-id="7a589-114">`GetStackParameterSize`在非 x86 平台上呼叫。</span><span class="sxs-lookup"><span data-stu-id="7a589-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="7a589-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7a589-115">E_FAIL</span></span>|<span data-ttu-id="7a589-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="7a589-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="7a589-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7a589-117">E_INVALIDARG</span></span>|<span data-ttu-id="7a589-118">`pSize`是`null`。</span><span class="sxs-lookup"><span data-stu-id="7a589-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="7a589-119">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7a589-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a589-120">備註</span><span class="sxs-lookup"><span data-stu-id="7a589-120">Remarks</span></span>  
 <span data-ttu-id="7a589-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)方法不會調整參數，推入堆疊的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="7a589-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="7a589-122">相反地，您可以使用所傳回的值`GetStackParameterSize`調整來植入原生回溯器，並調整參數的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="7a589-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a589-123">需求</span><span class="sxs-lookup"><span data-stu-id="7a589-123">Requirements</span></span>  
 <span data-ttu-id="7a589-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a589-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a589-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a589-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a589-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a589-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a589-127">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a589-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a589-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a589-128">See Also</span></span>  
 [<span data-ttu-id="7a589-129">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="7a589-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="7a589-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7a589-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7a589-131">偵錯</span><span class="sxs-lookup"><span data-stu-id="7a589-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
