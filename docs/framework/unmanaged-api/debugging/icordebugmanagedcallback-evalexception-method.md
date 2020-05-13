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
ms.openlocfilehash: 20a841006d51671a491e11c4e40287baf739d191
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209821"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="db708-102">ICorDebugManagedCallback::EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="db708-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="db708-103">通知偵錯工具，評估已結束，發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db708-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db708-104">語法</span><span class="sxs-lookup"><span data-stu-id="db708-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db708-105">參數</span><span class="sxs-lookup"><span data-stu-id="db708-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="db708-106">在ICorDebugAppDomain 物件的指標，代表評估終止的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="db708-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="db708-107">在ICorDebugThread 物件的指標，表示評估終止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="db708-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="db708-108">在ICorDebugEval 物件的指標，代表執行評估的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db708-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db708-109">需求</span><span class="sxs-lookup"><span data-stu-id="db708-109">Requirements</span></span>  
 <span data-ttu-id="db708-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db708-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db708-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db708-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db708-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db708-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db708-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db708-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db708-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="db708-114">See also</span></span>

- [<span data-ttu-id="db708-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="db708-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
