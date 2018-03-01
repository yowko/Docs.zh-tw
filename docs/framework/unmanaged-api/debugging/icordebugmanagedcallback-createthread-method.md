---
title: "ICorDebugManagedCallback::CreateThread 方法"
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
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8acb12d216949fc4e0636b5a2c28657ef5c79bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="b1d82-102">ICorDebugManagedCallback::CreateThread 方法</span><span class="sxs-lookup"><span data-stu-id="b1d82-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="b1d82-103">執行緒已開始執行 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b1d82-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d82-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1d82-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1d82-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1d82-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b1d82-106">[in]表示包含執行緒的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="b1d82-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="b1d82-107">[in]表示執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="b1d82-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1d82-108">備註</span><span class="sxs-lookup"><span data-stu-id="b1d82-108">Remarks</span></span>  
 <span data-ttu-id="b1d82-109">執行緒會位於第一個要執行的 managed 程式碼指令。</span><span class="sxs-lookup"><span data-stu-id="b1d82-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d82-110">需求</span><span class="sxs-lookup"><span data-stu-id="b1d82-110">Requirements</span></span>  
 <span data-ttu-id="b1d82-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1d82-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d82-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1d82-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1d82-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1d82-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1d82-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d82-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d82-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d82-115">See Also</span></span>  
 [<span data-ttu-id="b1d82-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b1d82-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
