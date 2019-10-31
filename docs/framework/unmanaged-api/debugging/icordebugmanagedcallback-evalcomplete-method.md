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
ms.openlocfilehash: d52c19f8663a776215241ddb16f3aa9ba00c0d36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137344"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="b28e4-102">ICorDebugManagedCallback::EvalComplete 方法</span><span class="sxs-lookup"><span data-stu-id="b28e4-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="b28e4-103">通知偵錯工具已完成評估。</span><span class="sxs-lookup"><span data-stu-id="b28e4-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="b28e4-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b28e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="b28e4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b28e4-106">在ICorDebugAppDomain 物件的指標，代表執行評估所在的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="b28e4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b28e4-107">在ICorDebugThread 物件的指標，代表執行評估的執行緒。</span><span class="sxs-lookup"><span data-stu-id="b28e4-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="b28e4-108">在ICorDebugEval 物件的指標，代表執行評估的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b28e4-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b28e4-109">需求</span><span class="sxs-lookup"><span data-stu-id="b28e4-109">Requirements</span></span>  
 <span data-ttu-id="b28e4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b28e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b28e4-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b28e4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b28e4-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b28e4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b28e4-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b28e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28e4-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b28e4-114">See also</span></span>

- [<span data-ttu-id="b28e4-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b28e4-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
