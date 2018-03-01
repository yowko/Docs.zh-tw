---
title: "ICorDebugManagedCallback::ExitThread 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6c39a8c92a8c0be8d0607663a833ac7307ca26d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="dffc8-102">ICorDebugManagedCallback::ExitThread 方法</span><span class="sxs-lookup"><span data-stu-id="dffc8-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="dffc8-103">告知偵錯工具正在執行 managed 程式碼的執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="dffc8-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="dffc8-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dffc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="dffc8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dffc8-106">[in]表示包含 managed 的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="dffc8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="dffc8-107">[in]表示 managed 的執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="dffc8-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dffc8-108">備註</span><span class="sxs-lookup"><span data-stu-id="dffc8-108">Remarks</span></span>  
 <span data-ttu-id="dffc8-109">一次`ExitThread`引發回呼時，執行緒不會再出現在執行緒列舉型別。</span><span class="sxs-lookup"><span data-stu-id="dffc8-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffc8-110">需求</span><span class="sxs-lookup"><span data-stu-id="dffc8-110">Requirements</span></span>  
 <span data-ttu-id="dffc8-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dffc8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dffc8-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dffc8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dffc8-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dffc8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dffc8-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dffc8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffc8-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="dffc8-115">See Also</span></span>  
 [<span data-ttu-id="dffc8-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dffc8-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
