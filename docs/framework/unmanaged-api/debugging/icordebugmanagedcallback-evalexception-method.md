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
ms.openlocfilehash: 602bcd12d1fd4c5806de6db81252731baa447b7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120012"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="a0a28-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="a0a28-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="a0a28-103">告知偵錯工具評估已結束並發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a0a28-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a28-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0a28-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0a28-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0a28-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a0a28-106">[in]表示評估已終止的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="a0a28-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a0a28-107">[in]ICorDebugThread 物件，表示已評估終止執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="a0a28-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="a0a28-108">[in]ICorDebugEval 物件，表示執行評估的程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="a0a28-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a28-109">需求</span><span class="sxs-lookup"><span data-stu-id="a0a28-109">Requirements</span></span>  
 <span data-ttu-id="a0a28-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a28-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a28-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0a28-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0a28-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0a28-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a0a28-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a0a28-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0a28-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0a28-114">See also</span></span>

- [<span data-ttu-id="a0a28-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a0a28-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
