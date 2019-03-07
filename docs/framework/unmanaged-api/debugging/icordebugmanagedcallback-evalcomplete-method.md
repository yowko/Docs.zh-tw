---
title: ICorDebugManagedCallback::EvalComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d5af8196664c63b26f3a10946b69ae922cf13fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503134"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="81129-102">ICorDebugManagedCallback::EvalComplete 方法</span><span class="sxs-lookup"><span data-stu-id="81129-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="81129-103">告知偵錯工具評估已完成。</span><span class="sxs-lookup"><span data-stu-id="81129-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81129-104">語法</span><span class="sxs-lookup"><span data-stu-id="81129-104">Syntax</span></span>  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81129-105">參數</span><span class="sxs-lookup"><span data-stu-id="81129-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="81129-106">[in]表示在其中評估已執行的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="81129-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="81129-107">[in]表示評估執行所在的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="81129-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="81129-108">[in]ICorDebugEval 物件，表示執行評估的程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="81129-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81129-109">需求</span><span class="sxs-lookup"><span data-stu-id="81129-109">Requirements</span></span>  
 <span data-ttu-id="81129-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81129-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81129-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81129-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81129-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81129-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81129-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81129-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81129-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81129-114">See also</span></span>
- [<span data-ttu-id="81129-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="81129-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
