---
title: "ICorDebug::Terminate 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e416f8ea20bde49a1c1cdb5d61bc4a6bfbce7913
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="51b95-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="51b95-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="51b95-103">終止`ICorDebug`物件。</span><span class="sxs-lookup"><span data-stu-id="51b95-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51b95-104">`Terminate`不應該呼叫直到[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回呼已收到所有正在偵錯的處理程序。</span><span class="sxs-lookup"><span data-stu-id="51b95-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b95-105">語法</span><span class="sxs-lookup"><span data-stu-id="51b95-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="51b95-106">備註</span><span class="sxs-lookup"><span data-stu-id="51b95-106">Remarks</span></span>  
 <span data-ttu-id="51b95-107">`Terminate`時，必須呼叫`ICorDebug`不再需要物件。</span><span class="sxs-lookup"><span data-stu-id="51b95-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b95-108">需求</span><span class="sxs-lookup"><span data-stu-id="51b95-108">Requirements</span></span>  
 <span data-ttu-id="51b95-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51b95-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b95-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51b95-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51b95-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51b95-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b95-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b95-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b95-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="51b95-113">See Also</span></span>  
 [<span data-ttu-id="51b95-114">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="51b95-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
