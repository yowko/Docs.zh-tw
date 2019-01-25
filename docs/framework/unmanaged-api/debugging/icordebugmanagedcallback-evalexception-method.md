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
ms.openlocfilehash: 1705b9d77d0d91196201d713cceb0ccf0f8635a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728011"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="bd0bc-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="bd0bc-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="bd0bc-103">告知偵錯工具評估已結束並發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd0bc-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd0bc-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd0bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd0bc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bd0bc-106">[in]表示評估已終止的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="bd0bc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="bd0bc-107">[in]ICorDebugThread 物件，表示已評估終止執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="bd0bc-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="bd0bc-108">[in]ICorDebugEval 物件，表示執行評估的程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="bd0bc-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd0bc-109">需求</span><span class="sxs-lookup"><span data-stu-id="bd0bc-109">Requirements</span></span>  
 <span data-ttu-id="bd0bc-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd0bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd0bc-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd0bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd0bc-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd0bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd0bc-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd0bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0bc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd0bc-114">See also</span></span>
- [<span data-ttu-id="bd0bc-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bd0bc-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
