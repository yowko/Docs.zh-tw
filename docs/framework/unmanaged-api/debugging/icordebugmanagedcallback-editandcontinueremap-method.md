---
title: ICorDebugManagedCallback::EditAndContinueRemap 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 100688ece4ebb984d3d03823ab01bbaae7d395db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760278"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="773c2-102">ICorDebugManagedCallback::EditAndContinueRemap 方法</span><span class="sxs-lookup"><span data-stu-id="773c2-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="773c2-103">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="773c2-103">This method has been deprecated.</span></span> <span data-ttu-id="773c2-104">它會通知偵錯工具，已重新對應事件傳送至整合式的開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="773c2-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="773c2-105">語法</span><span class="sxs-lookup"><span data-stu-id="773c2-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="773c2-106">備註</span><span class="sxs-lookup"><span data-stu-id="773c2-106">Remarks</span></span>  
 <span data-ttu-id="773c2-107">`EditAndContinueRemap`已嘗試的舊版本的更新函式中的程式碼執行時，會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="773c2-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="773c2-108">通用語言執行階段會呼叫`EditAndContinueRemap`ide 傳送重新對應事件的方法。</span><span class="sxs-lookup"><span data-stu-id="773c2-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="773c2-109">需求</span><span class="sxs-lookup"><span data-stu-id="773c2-109">Requirements</span></span>  
 <span data-ttu-id="773c2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="773c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="773c2-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="773c2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="773c2-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="773c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="773c2-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="773c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="773c2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="773c2-114">See also</span></span>

- [<span data-ttu-id="773c2-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="773c2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
