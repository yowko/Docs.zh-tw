---
title: ICorDebugManagedCallback::StepComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50bb5312b294a3e92ab945c3f0443a4eb81d133
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634422"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="8b279-102">ICorDebugManagedCallback::StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="8b279-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="8b279-103">已完成步驟會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8b279-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b279-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b279-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b279-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b279-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8b279-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含的步驟執行完畢的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="8b279-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8b279-107">[in]ICorDebugThread 物件，表示步驟執行完畢的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="8b279-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="8b279-108">[in]ICorDebugStepper 物件，表示執行程式碼中的步驟指標。</span><span class="sxs-lookup"><span data-stu-id="8b279-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="8b279-109">[in]CorDebugStepReason 列舉，指出個別步驟的結果值。</span><span class="sxs-lookup"><span data-stu-id="8b279-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b279-110">備註</span><span class="sxs-lookup"><span data-stu-id="8b279-110">Remarks</span></span>  
 <span data-ttu-id="8b279-111">步進可能可用來繼續逐步執行如有需要，除非偵錯已終止。</span><span class="sxs-lookup"><span data-stu-id="8b279-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b279-112">需求</span><span class="sxs-lookup"><span data-stu-id="8b279-112">Requirements</span></span>  
 <span data-ttu-id="8b279-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b279-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b279-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b279-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b279-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b279-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b279-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b279-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b279-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b279-117">See also</span></span>
- [<span data-ttu-id="8b279-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8b279-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
