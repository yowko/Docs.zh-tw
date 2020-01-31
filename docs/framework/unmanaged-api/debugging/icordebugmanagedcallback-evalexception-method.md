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
ms.openlocfilehash: 3ae93081bd201f745fa47bc01a9c6fcbf6e9f63c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781866"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="cc881-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="cc881-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="cc881-103">通知偵錯工具，評估已結束，發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cc881-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc881-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc881-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc881-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc881-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cc881-106">在ICorDebugAppDomain 物件的指標，代表評估終止的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="cc881-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cc881-107">在ICorDebugThread 物件的指標，表示評估終止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="cc881-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="cc881-108">在ICorDebugEval 物件的指標，代表執行評估的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc881-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc881-109">需求</span><span class="sxs-lookup"><span data-stu-id="cc881-109">Requirements</span></span>  
 <span data-ttu-id="cc881-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc881-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc881-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc881-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc881-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc881-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc881-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc881-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc881-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc881-114">See also</span></span>

- [<span data-ttu-id="cc881-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cc881-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
