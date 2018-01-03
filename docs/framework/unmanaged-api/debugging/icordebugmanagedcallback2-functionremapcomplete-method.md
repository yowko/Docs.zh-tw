---
title: "ICorDebugManagedCallback2::FunctionRemapComplete 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52c7ead9091754d4355880befe6a8a11b3cc5eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="d14ba-102">ICorDebugManagedCallback2::FunctionRemapComplete 方法</span><span class="sxs-lookup"><span data-stu-id="d14ba-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="d14ba-103">告知偵錯工具執行程式碼已切換為編輯的函式的新版本。</span><span class="sxs-lookup"><span data-stu-id="d14ba-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="d14ba-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d14ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="d14ba-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d14ba-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含編輯函式指標。</span><span class="sxs-lookup"><span data-stu-id="d14ba-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d14ba-107">[in]表示執行緒在其發現重新對應中斷點的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="d14ba-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="d14ba-108">[in]ICorDebugFunction 物件，表示目前執行緒上執行的函式版本指標。</span><span class="sxs-lookup"><span data-stu-id="d14ba-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d14ba-109">備註</span><span class="sxs-lookup"><span data-stu-id="d14ba-109">Remarks</span></span>  
 <span data-ttu-id="d14ba-110">此回呼會讓偵錯工具來重新建立先前存在於任何 stepper 有機會。</span><span class="sxs-lookup"><span data-stu-id="d14ba-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d14ba-111">需求</span><span class="sxs-lookup"><span data-stu-id="d14ba-111">Requirements</span></span>  
 <span data-ttu-id="d14ba-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d14ba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d14ba-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d14ba-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d14ba-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d14ba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d14ba-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d14ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14ba-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d14ba-116">See Also</span></span>  
 [<span data-ttu-id="d14ba-117">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="d14ba-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="d14ba-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d14ba-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
