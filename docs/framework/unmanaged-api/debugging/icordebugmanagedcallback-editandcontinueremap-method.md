---
title: "ICorDebugManagedCallback::EditAndContinueRemap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EditAndContinueRemap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e45cf5376f0c8b4fbe76f56e3adcce22b1ef5c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="18aa2-102">ICorDebugManagedCallback::EditAndContinueRemap 方法</span><span class="sxs-lookup"><span data-stu-id="18aa2-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="18aa2-103">這個方法已被取代。</span><span class="sxs-lookup"><span data-stu-id="18aa2-103">This method has been deprecated.</span></span> <span data-ttu-id="18aa2-104">它會通知偵錯工具，已重新對應事件傳送至整合式的開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="18aa2-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18aa2-105">語法</span><span class="sxs-lookup"><span data-stu-id="18aa2-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="18aa2-106">備註</span><span class="sxs-lookup"><span data-stu-id="18aa2-106">Remarks</span></span>  
 <span data-ttu-id="18aa2-107">`EditAndContinueRemap`時嘗試執行較舊版本的更新函式中的程式碼呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="18aa2-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="18aa2-108">通用語言執行階段呼叫`EditAndContinueRemap`傳送 ide 的重新對應事件的方法。</span><span class="sxs-lookup"><span data-stu-id="18aa2-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18aa2-109">需求</span><span class="sxs-lookup"><span data-stu-id="18aa2-109">Requirements</span></span>  
 <span data-ttu-id="18aa2-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18aa2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18aa2-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18aa2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18aa2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18aa2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18aa2-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18aa2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18aa2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18aa2-114">See Also</span></span>  
 [<span data-ttu-id="18aa2-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="18aa2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
