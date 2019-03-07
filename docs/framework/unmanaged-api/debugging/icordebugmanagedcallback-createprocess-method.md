---
title: ICorDebugManagedCallback::CreateProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36e26101a21471fd840a07deef9f5085a88f2730
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487027"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="cecf9-102">ICorDebugManagedCallback::CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="cecf9-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="cecf9-103">已附加或第一次啟動處理程序時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cecf9-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecf9-104">語法</span><span class="sxs-lookup"><span data-stu-id="cecf9-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cecf9-105">參數</span><span class="sxs-lookup"><span data-stu-id="cecf9-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="cecf9-106">[in]表示已附加或啟動的處理序的 ICorDebugProcess 物件指標。</span><span class="sxs-lookup"><span data-stu-id="cecf9-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cecf9-107">備註</span><span class="sxs-lookup"><span data-stu-id="cecf9-107">Remarks</span></span>  
 <span data-ttu-id="cecf9-108">直到初始化 common language runtime，不會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="cecf9-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="cecf9-109">大部分[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法會傳回前的 CORDBG_E_NOTREADY`CreateProcess`回呼。</span><span class="sxs-lookup"><span data-stu-id="cecf9-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecf9-110">需求</span><span class="sxs-lookup"><span data-stu-id="cecf9-110">Requirements</span></span>  
 <span data-ttu-id="cecf9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cecf9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cecf9-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cecf9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cecf9-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cecf9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cecf9-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cecf9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecf9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cecf9-115">See also</span></span>
- [<span data-ttu-id="cecf9-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cecf9-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
