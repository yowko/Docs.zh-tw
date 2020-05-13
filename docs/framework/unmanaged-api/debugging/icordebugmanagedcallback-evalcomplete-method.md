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
ms.openlocfilehash: 0431b54997c9889e2b3206392e86e4dcde45ffb3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212447"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="deada-102">ICorDebugManagedCallback::EvalComplete 方法</span><span class="sxs-lookup"><span data-stu-id="deada-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="deada-103">通知偵錯工具已完成評估。</span><span class="sxs-lookup"><span data-stu-id="deada-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deada-104">語法</span><span class="sxs-lookup"><span data-stu-id="deada-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deada-105">參數</span><span class="sxs-lookup"><span data-stu-id="deada-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="deada-106">在ICorDebugAppDomain 物件的指標，代表執行評估所在的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="deada-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="deada-107">在ICorDebugThread 物件的指標，代表執行評估的執行緒。</span><span class="sxs-lookup"><span data-stu-id="deada-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="deada-108">在ICorDebugEval 物件的指標，代表執行評估的程式碼。</span><span class="sxs-lookup"><span data-stu-id="deada-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deada-109">需求</span><span class="sxs-lookup"><span data-stu-id="deada-109">Requirements</span></span>  
 <span data-ttu-id="deada-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="deada-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deada-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="deada-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deada-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deada-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deada-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deada-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deada-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="deada-114">See also</span></span>

- [<span data-ttu-id="deada-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="deada-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
