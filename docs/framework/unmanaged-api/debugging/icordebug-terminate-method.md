---
title: ICorDebug::Terminate 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: cf9c9d11c4725908fcf7ff4a0c91882b70a80190
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723372"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="e8978-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="e8978-102">ICorDebug::Terminate Method</span></span>

<span data-ttu-id="e8978-103">終止 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="e8978-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8978-104">`Terminate` 必須等到針對所有正在進行的處理常式接收到 [ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md) 回呼之後，才應該呼叫。</span><span class="sxs-lookup"><span data-stu-id="e8978-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8978-105">語法</span><span class="sxs-lookup"><span data-stu-id="e8978-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8978-106">備註</span><span class="sxs-lookup"><span data-stu-id="e8978-106">Remarks</span></span>  

 <span data-ttu-id="e8978-107">`Terminate` 當不再需要物件時，必須呼叫 `ICorDebug` 。</span><span class="sxs-lookup"><span data-stu-id="e8978-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8978-108">需求</span><span class="sxs-lookup"><span data-stu-id="e8978-108">Requirements</span></span>  

 <span data-ttu-id="e8978-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8978-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8978-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8978-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8978-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8978-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8978-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8978-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8978-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8978-113">See also</span></span>

- [<span data-ttu-id="e8978-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="e8978-114">ICorDebug Interface</span></span>](icordebug-interface.md)
