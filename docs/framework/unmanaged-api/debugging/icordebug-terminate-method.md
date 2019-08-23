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
ms.openlocfilehash: de37bb34aee9b6536ff892ac30855761bcc69445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963135"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="c475f-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="c475f-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="c475f-103">`ICorDebug`終止物件。</span><span class="sxs-lookup"><span data-stu-id="c475f-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c475f-104">`Terminate`必須等到針對所有正在進行調試的進程收到[ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回呼之後, 才能呼叫。</span><span class="sxs-lookup"><span data-stu-id="c475f-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c475f-105">語法</span><span class="sxs-lookup"><span data-stu-id="c475f-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c475f-106">備註</span><span class="sxs-lookup"><span data-stu-id="c475f-106">Remarks</span></span>  
 <span data-ttu-id="c475f-107">`Terminate`當不再需要物件時`ICorDebug` , 必須呼叫。</span><span class="sxs-lookup"><span data-stu-id="c475f-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c475f-108">需求</span><span class="sxs-lookup"><span data-stu-id="c475f-108">Requirements</span></span>  
 <span data-ttu-id="c475f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c475f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c475f-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c475f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c475f-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c475f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c475f-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c475f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c475f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c475f-113">See also</span></span>

- [<span data-ttu-id="c475f-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="c475f-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
