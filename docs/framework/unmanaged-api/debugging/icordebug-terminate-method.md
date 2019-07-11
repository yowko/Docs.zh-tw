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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3037fc704ffc3aac4d050cef7857261f138f7d35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738066"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="c524f-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="c524f-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="c524f-103">終止`ICorDebug`物件。</span><span class="sxs-lookup"><span data-stu-id="c524f-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c524f-104">`Terminate` 之前，不應該呼叫[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回呼已收到所有正在偵錯的處理程序。</span><span class="sxs-lookup"><span data-stu-id="c524f-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c524f-105">語法</span><span class="sxs-lookup"><span data-stu-id="c524f-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c524f-106">備註</span><span class="sxs-lookup"><span data-stu-id="c524f-106">Remarks</span></span>  
 <span data-ttu-id="c524f-107">`Terminate` 時，必須呼叫`ICorDebug`不再需要物件。</span><span class="sxs-lookup"><span data-stu-id="c524f-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c524f-108">需求</span><span class="sxs-lookup"><span data-stu-id="c524f-108">Requirements</span></span>  
 <span data-ttu-id="c524f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c524f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c524f-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c524f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c524f-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c524f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c524f-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c524f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c524f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c524f-113">See also</span></span>

- [<span data-ttu-id="c524f-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="c524f-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
