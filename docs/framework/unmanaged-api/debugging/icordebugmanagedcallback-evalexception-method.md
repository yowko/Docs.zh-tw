---
title: ICorDebugManagedCallback::EvalException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbf12612bb432f8935d08bdeac0bbcb471c38c54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759635"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="c4c46-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="c4c46-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="c4c46-103">告知偵錯工具評估已結束並發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4c46-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c46-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4c46-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4c46-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4c46-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c4c46-106">[in]表示評估已終止的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="c4c46-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c4c46-107">[in]ICorDebugThread 物件，表示已評估終止執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="c4c46-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="c4c46-108">[in]ICorDebugEval 物件，表示執行評估的程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="c4c46-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c46-109">需求</span><span class="sxs-lookup"><span data-stu-id="c4c46-109">Requirements</span></span>  
 <span data-ttu-id="c4c46-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c46-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c46-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4c46-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4c46-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4c46-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4c46-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c46-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c46-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c46-114">See also</span></span>

- [<span data-ttu-id="c4c46-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c4c46-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
