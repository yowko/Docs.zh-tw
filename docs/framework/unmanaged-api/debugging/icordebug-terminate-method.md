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
ms.openlocfilehash: 78838e9002cb3f5263395af9de255c54de47b6ae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134022"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="3259e-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="3259e-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="3259e-103">終止 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="3259e-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3259e-104">在針對所有正在進行調試的進程收到[ICorDebugManagedCallback：： ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回呼之前，不應呼叫 `Terminate`。</span><span class="sxs-lookup"><span data-stu-id="3259e-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3259e-105">語法</span><span class="sxs-lookup"><span data-stu-id="3259e-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3259e-106">備註</span><span class="sxs-lookup"><span data-stu-id="3259e-106">Remarks</span></span>  
 <span data-ttu-id="3259e-107">當不再需要 `ICorDebug` 物件時，必須呼叫 `Terminate`。</span><span class="sxs-lookup"><span data-stu-id="3259e-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3259e-108">需求</span><span class="sxs-lookup"><span data-stu-id="3259e-108">Requirements</span></span>  
 <span data-ttu-id="3259e-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3259e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3259e-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3259e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3259e-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3259e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3259e-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3259e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3259e-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3259e-113">See also</span></span>

- [<span data-ttu-id="3259e-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="3259e-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
