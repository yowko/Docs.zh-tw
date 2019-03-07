---
title: ICorDebugThread2::InterceptCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b883a5c6dd0cff119ff09747d32c607ac7ec60
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500989"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="5a63c-102">ICorDebugThread2::InterceptCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="5a63c-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="5a63c-103">可讓偵錯工具攔截目前的例外狀況，在此執行緒。</span><span class="sxs-lookup"><span data-stu-id="5a63c-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a63c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a63c-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a63c-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a63c-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="5a63c-106">[in]ICorDebugFrame，表示作用中堆疊框架指標。</span><span class="sxs-lookup"><span data-stu-id="5a63c-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a63c-107">備註</span><span class="sxs-lookup"><span data-stu-id="5a63c-107">Remarks</span></span>  
 <span data-ttu-id="5a63c-108">`InterceptCurrentException`之間的例外狀況的回呼，可以呼叫方法 ([icordebugmanagedcallback:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)或是[ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) 和相關聯的呼叫來[Icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5a63c-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a63c-109">需求</span><span class="sxs-lookup"><span data-stu-id="5a63c-109">Requirements</span></span>  
 <span data-ttu-id="5a63c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a63c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a63c-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a63c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a63c-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a63c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a63c-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a63c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
