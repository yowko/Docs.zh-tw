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
ms.openlocfilehash: 4414bab535b63f55a580e93cc6de9cb0dedc073c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415512"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="2722e-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="2722e-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="2722e-103">告知偵錯工具評估已結束，發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2722e-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2722e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2722e-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2722e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2722e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2722e-106">[in]代表應用程式定義域中結束評估 ICorDebugAppDomain 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2722e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2722e-107">[in]表示評估已終止執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2722e-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="2722e-108">[in]表示執行評估的程式碼 ICorDebugEval 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2722e-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2722e-109">需求</span><span class="sxs-lookup"><span data-stu-id="2722e-109">Requirements</span></span>  
 <span data-ttu-id="2722e-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2722e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2722e-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2722e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2722e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2722e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2722e-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2722e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2722e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2722e-114">See Also</span></span>  
 [<span data-ttu-id="2722e-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2722e-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
