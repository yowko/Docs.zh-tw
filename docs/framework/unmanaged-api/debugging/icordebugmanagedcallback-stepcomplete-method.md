---
title: "ICorDebugManagedCallback::StepComplete 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.StepComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e7a09216284593c79c0cda6f5283ea8250678af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="2461e-102">ICorDebugManagedCallback::StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="2461e-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="2461e-103">告知偵錯工具已完成步驟。</span><span class="sxs-lookup"><span data-stu-id="2461e-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2461e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2461e-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2461e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2461e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2461e-106">[in]表示包含在步驟中完成的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="2461e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2461e-107">[in]表示完成步驟的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2461e-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="2461e-108">[in]表示執行程式碼中的步驟 ICorDebugStepper 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2461e-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="2461e-109">[in]CorDebugStepReason 列舉，指出個別步驟的結果值。</span><span class="sxs-lookup"><span data-stu-id="2461e-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2461e-110">備註</span><span class="sxs-lookup"><span data-stu-id="2461e-110">Remarks</span></span>  
 <span data-ttu-id="2461e-111">Stepper 可能用於繼續逐步執行如有需要，除非偵錯已終止。</span><span class="sxs-lookup"><span data-stu-id="2461e-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2461e-112">需求</span><span class="sxs-lookup"><span data-stu-id="2461e-112">Requirements</span></span>  
 <span data-ttu-id="2461e-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2461e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2461e-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2461e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2461e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2461e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2461e-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2461e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2461e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2461e-117">See Also</span></span>  
 [<span data-ttu-id="2461e-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2461e-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
