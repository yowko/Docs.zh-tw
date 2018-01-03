---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 208803acea65b24429938dc646e7abe70949b237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="f0cfd-102">ICorDebugManagedCallback2::FunctionRemapOpportunity 方法</span><span class="sxs-lookup"><span data-stu-id="f0cfd-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="f0cfd-103">告知偵錯工具執行程式碼已達到較舊版本的已編輯函式中的序列點。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0cfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0cfd-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0cfd-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0cfd-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f0cfd-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含編輯函式指標。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f0cfd-107">[in]表示執行緒在其發現重新對應中斷點的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="f0cfd-108">[in]ICorDebugFunction 物件，表示目前的執行緒執行的函式版本指標。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="f0cfd-109">[in]ICorDebugFunction 物件，表示最新版本的函式指標。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="f0cfd-110">[in]指令指標的函式的舊版本中的 Microsoft intermediate language (MSIL) 位移。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0cfd-111">備註</span><span class="sxs-lookup"><span data-stu-id="f0cfd-111">Remarks</span></span>  
 <span data-ttu-id="f0cfd-112">此回呼會讓偵錯工具呼叫來重新對應其適當的位置中指定的函式的新版本的指令指標[icordebugilframe2:: Remapfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="f0cfd-113">如果偵錯工具不會呼叫`RemapFunction`之前先呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法，執行階段將會繼續執行舊的程式碼，而且會引發另一個`FunctionRemapOpportunity`回呼，在下一個序列點。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="f0cfd-114">每個框架正在執行較舊版本的指定函式，直到偵錯工具傳回 S_OK 時，會叫用這個回呼。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0cfd-115">需求</span><span class="sxs-lookup"><span data-stu-id="f0cfd-115">Requirements</span></span>  
 <span data-ttu-id="f0cfd-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0cfd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0cfd-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0cfd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0cfd-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0cfd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0cfd-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0cfd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cfd-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0cfd-120">See Also</span></span>  
 [<span data-ttu-id="f0cfd-121">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="f0cfd-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="f0cfd-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f0cfd-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
