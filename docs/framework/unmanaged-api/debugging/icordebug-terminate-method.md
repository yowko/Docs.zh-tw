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
ms.openlocfilehash: 321298ce942b35d11a861c87cdf6b8714179ea97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080829"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="7eab1-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="7eab1-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="7eab1-103">終止`ICorDebug`物件。</span><span class="sxs-lookup"><span data-stu-id="7eab1-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  `Terminate` <span data-ttu-id="7eab1-104">之前，不應該呼叫[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回呼已收到所有正在偵錯的處理程序。</span><span class="sxs-lookup"><span data-stu-id="7eab1-104">should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eab1-105">語法</span><span class="sxs-lookup"><span data-stu-id="7eab1-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7eab1-106">備註</span><span class="sxs-lookup"><span data-stu-id="7eab1-106">Remarks</span></span>  
 `Terminate` <span data-ttu-id="7eab1-107">時，必須呼叫`ICorDebug`不再需要物件。</span><span class="sxs-lookup"><span data-stu-id="7eab1-107">must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eab1-108">需求</span><span class="sxs-lookup"><span data-stu-id="7eab1-108">Requirements</span></span>  
 <span data-ttu-id="7eab1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7eab1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eab1-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eab1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eab1-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eab1-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7eab1-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7eab1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7eab1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eab1-113">See also</span></span>

- [<span data-ttu-id="7eab1-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="7eab1-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
