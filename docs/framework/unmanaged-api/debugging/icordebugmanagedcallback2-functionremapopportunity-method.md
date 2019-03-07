---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ab6dac8302d4e03f5d8adad1267f209f131c00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476475"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="efb13-102">ICorDebugManagedCallback2::FunctionRemapOpportunity 方法</span><span class="sxs-lookup"><span data-stu-id="efb13-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="efb13-103">告知偵錯工具執行程式碼已達到較舊版本的已編輯的函式中的序列點。</span><span class="sxs-lookup"><span data-stu-id="efb13-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb13-104">語法</span><span class="sxs-lookup"><span data-stu-id="efb13-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efb13-105">參數</span><span class="sxs-lookup"><span data-stu-id="efb13-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="efb13-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含已編輯的函式指標。</span><span class="sxs-lookup"><span data-stu-id="efb13-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="efb13-107">[in]ICorDebugThread 物件，表示在其發現重新對應中斷點的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="efb13-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="efb13-108">[in]ICorDebugFunction 物件，表示目前執行緒上執行的函式版本的指標。</span><span class="sxs-lookup"><span data-stu-id="efb13-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="efb13-109">[in]ICorDebugFunction 物件，表示最新版本的函式指標。</span><span class="sxs-lookup"><span data-stu-id="efb13-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="efb13-110">[in]Microsoft intermediate language (MSIL) 位移的函式的舊版本中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="efb13-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efb13-111">備註</span><span class="sxs-lookup"><span data-stu-id="efb13-111">Remarks</span></span>  
 <span data-ttu-id="efb13-112">此回呼會讓偵錯工具重新對應指令指標至其適當的位置，在新版本中所指定函式藉由呼叫[ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="efb13-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="efb13-113">如果偵錯工具不會呼叫`RemapFunction`呼叫之前，先[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法，執行階段將會繼續執行舊的程式碼，並會引發另一個`FunctionRemapOpportunity`回呼，在下一個序列點。</span><span class="sxs-lookup"><span data-stu-id="efb13-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="efb13-114">每個框架正在執行較舊版本的指定的函式，直到偵錯工具會傳回 s_ok 時，會叫用這個回呼。</span><span class="sxs-lookup"><span data-stu-id="efb13-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efb13-115">需求</span><span class="sxs-lookup"><span data-stu-id="efb13-115">Requirements</span></span>  
 <span data-ttu-id="efb13-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efb13-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efb13-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efb13-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efb13-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efb13-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efb13-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efb13-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb13-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efb13-120">See also</span></span>
- [<span data-ttu-id="efb13-121">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="efb13-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="efb13-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="efb13-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
