---
title: ICorDebugManagedCallback::ExitThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85247f2f3672e7827f4dd0c93e50cd5da914ee8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755772"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="6bc66-102">ICorDebugManagedCallback::ExitThread 方法</span><span class="sxs-lookup"><span data-stu-id="6bc66-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="6bc66-103">已結束執行緒所執行的 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="6bc66-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc66-104">語法</span><span class="sxs-lookup"><span data-stu-id="6bc66-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bc66-105">參數</span><span class="sxs-lookup"><span data-stu-id="6bc66-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6bc66-106">[in]表示包含 managed 的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="6bc66-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="6bc66-107">[in]ICorDebugThread 物件，表示 managed 的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="6bc66-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bc66-108">備註</span><span class="sxs-lookup"><span data-stu-id="6bc66-108">Remarks</span></span>  
 <span data-ttu-id="6bc66-109">一次`ExitThread`引發回呼時，執行緒不會再出現在 執行緒列舉型別。</span><span class="sxs-lookup"><span data-stu-id="6bc66-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bc66-110">需求</span><span class="sxs-lookup"><span data-stu-id="6bc66-110">Requirements</span></span>  
 <span data-ttu-id="6bc66-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc66-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc66-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bc66-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bc66-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bc66-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bc66-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc66-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc66-115">See also</span></span>

- [<span data-ttu-id="6bc66-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6bc66-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
