---
title: ICorDebugManagedCallback::EditAndContinueRemap 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 9cb956c0262fdcdb5971d049ea7b057aa4d952c0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781898"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="d062b-102">ICorDebugManagedCallback::EditAndContinueRemap 方法</span><span class="sxs-lookup"><span data-stu-id="d062b-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="d062b-103">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="d062b-103">This method has been deprecated.</span></span> <span data-ttu-id="d062b-104">它會通知偵錯工具已將重新對應事件傳送至整合式開發環境（IDE）。</span><span class="sxs-lookup"><span data-stu-id="d062b-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d062b-105">語法</span><span class="sxs-lookup"><span data-stu-id="d062b-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d062b-106">備註</span><span class="sxs-lookup"><span data-stu-id="d062b-106">Remarks</span></span>  
 <span data-ttu-id="d062b-107">嘗試執行舊版更新函式中的程式碼時，會呼叫 `EditAndContinueRemap` 方法。</span><span class="sxs-lookup"><span data-stu-id="d062b-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="d062b-108">Common language runtime 會呼叫 `EditAndContinueRemap` 方法，將重新對應事件傳送至 IDE。</span><span class="sxs-lookup"><span data-stu-id="d062b-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d062b-109">需求</span><span class="sxs-lookup"><span data-stu-id="d062b-109">Requirements</span></span>  
 <span data-ttu-id="d062b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d062b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d062b-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d062b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d062b-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d062b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d062b-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d062b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d062b-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d062b-114">See also</span></span>

- [<span data-ttu-id="d062b-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d062b-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
