---
title: ICorDebugManagedCallback2::FunctionRemapComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9920627ed193e9741d65fddfc54f325cb1d3758c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761055"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="7fcc7-102">ICorDebugManagedCallback2::FunctionRemapComplete 方法</span><span class="sxs-lookup"><span data-stu-id="7fcc7-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="7fcc7-103">執行程式碼已切換為新版的已編輯的函式會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7fcc7-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fcc7-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fcc7-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fcc7-105">參數</span><span class="sxs-lookup"><span data-stu-id="7fcc7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7fcc7-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含已編輯的函式指標。</span><span class="sxs-lookup"><span data-stu-id="7fcc7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7fcc7-107">[in]ICorDebugThread 物件，表示在其發現重新對應中斷點的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="7fcc7-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="7fcc7-108">[in]ICorDebugFunction 物件，表示目前執行緒上執行的函式版本指標。</span><span class="sxs-lookup"><span data-stu-id="7fcc7-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fcc7-109">備註</span><span class="sxs-lookup"><span data-stu-id="7fcc7-109">Remarks</span></span>  
 <span data-ttu-id="7fcc7-110">此回呼會讓偵錯工具來重新建立先前存在於任何 steppers。</span><span class="sxs-lookup"><span data-stu-id="7fcc7-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fcc7-111">需求</span><span class="sxs-lookup"><span data-stu-id="7fcc7-111">Requirements</span></span>  
 <span data-ttu-id="7fcc7-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7fcc7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fcc7-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fcc7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fcc7-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fcc7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fcc7-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fcc7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fcc7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fcc7-116">See also</span></span>

- [<span data-ttu-id="7fcc7-117">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="7fcc7-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="7fcc7-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7fcc7-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
