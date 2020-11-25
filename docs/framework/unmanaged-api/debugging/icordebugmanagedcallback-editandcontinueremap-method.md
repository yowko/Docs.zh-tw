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
ms.openlocfilehash: 1d8aa2cca9dbbeaa9e03813b177ca59125770803
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721279"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="ff1b9-102">ICorDebugManagedCallback::EditAndContinueRemap 方法</span><span class="sxs-lookup"><span data-stu-id="ff1b9-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="ff1b9-103">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="ff1b9-103">This method has been deprecated.</span></span> <span data-ttu-id="ff1b9-104">它會通知偵錯工具，重新對應的事件已傳送至 (IDE) 的整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="ff1b9-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1b9-105">語法</span><span class="sxs-lookup"><span data-stu-id="ff1b9-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ff1b9-106">備註</span><span class="sxs-lookup"><span data-stu-id="ff1b9-106">Remarks</span></span>  

 <span data-ttu-id="ff1b9-107">`EditAndContinueRemap`嘗試在舊版更新函式中執行程式碼時，會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ff1b9-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="ff1b9-108">Common language runtime 會呼叫 `EditAndContinueRemap` 方法，以傳送重新對應事件至 IDE。</span><span class="sxs-lookup"><span data-stu-id="ff1b9-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff1b9-109">需求</span><span class="sxs-lookup"><span data-stu-id="ff1b9-109">Requirements</span></span>  

 <span data-ttu-id="ff1b9-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff1b9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff1b9-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff1b9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff1b9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff1b9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff1b9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff1b9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1b9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff1b9-114">See also</span></span>

- [<span data-ttu-id="ff1b9-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ff1b9-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
