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
ms.openlocfilehash: 70ae72968c3411a6732b09c0afe3d82931410cb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130808"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="132bf-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="132bf-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="132bf-103">通知偵錯工具，評估已結束，發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="132bf-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="132bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="132bf-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="132bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="132bf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="132bf-106">在ICorDebugAppDomain 物件的指標，代表評估終止的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="132bf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="132bf-107">在ICorDebugThread 物件的指標，表示評估終止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="132bf-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="132bf-108">在ICorDebugEval 物件的指標，代表執行評估的程式碼。</span><span class="sxs-lookup"><span data-stu-id="132bf-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="132bf-109">需求</span><span class="sxs-lookup"><span data-stu-id="132bf-109">Requirements</span></span>  
 <span data-ttu-id="132bf-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="132bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="132bf-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="132bf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="132bf-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="132bf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="132bf-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="132bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132bf-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="132bf-114">See also</span></span>

- [<span data-ttu-id="132bf-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="132bf-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
