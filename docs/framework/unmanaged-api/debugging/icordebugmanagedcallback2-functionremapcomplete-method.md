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
ms.openlocfilehash: cee712c2ff8acf56049ca9e288fad21e4608da3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="17bd4-102">ICorDebugManagedCallback2::FunctionRemapComplete 方法</span><span class="sxs-lookup"><span data-stu-id="17bd4-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="17bd4-103">告知偵錯工具執行程式碼已切換為編輯的函式的新版本。</span><span class="sxs-lookup"><span data-stu-id="17bd4-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="17bd4-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17bd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="17bd4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="17bd4-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含編輯函式指標。</span><span class="sxs-lookup"><span data-stu-id="17bd4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="17bd4-107">[in]表示執行緒在其發現重新對應中斷點的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="17bd4-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="17bd4-108">[in]ICorDebugFunction 物件，表示目前執行緒上執行的函式版本指標。</span><span class="sxs-lookup"><span data-stu-id="17bd4-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17bd4-109">備註</span><span class="sxs-lookup"><span data-stu-id="17bd4-109">Remarks</span></span>  
 <span data-ttu-id="17bd4-110">此回呼會讓偵錯工具來重新建立先前存在於任何 stepper 有機會。</span><span class="sxs-lookup"><span data-stu-id="17bd4-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17bd4-111">需求</span><span class="sxs-lookup"><span data-stu-id="17bd4-111">Requirements</span></span>  
 <span data-ttu-id="17bd4-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17bd4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17bd4-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17bd4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17bd4-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17bd4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17bd4-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17bd4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bd4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17bd4-116">See Also</span></span>  
 [<span data-ttu-id="17bd4-117">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="17bd4-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="17bd4-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="17bd4-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
