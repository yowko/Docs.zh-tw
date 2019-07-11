---
title: ICorDebug::SetManagedHandler 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90eb63b277f5c40053ecc3939890c87adc145251
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738127"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="abafa-102">ICorDebug::SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="abafa-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="abafa-103">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="abafa-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abafa-104">語法</span><span class="sxs-lookup"><span data-stu-id="abafa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abafa-105">參數</span><span class="sxs-lookup"><span data-stu-id="abafa-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="abafa-106">[in]指標[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)物件，也就是事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="abafa-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abafa-107">備註</span><span class="sxs-lookup"><span data-stu-id="abafa-107">Remarks</span></span>  
 <span data-ttu-id="abafa-108">`SetManagedHandler` 必須在建立時呼叫。</span><span class="sxs-lookup"><span data-stu-id="abafa-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="abafa-109">如果`ICorDebugManagedCallback`實作不包含足夠的介面，以處理應用程式進行偵錯，偵錯事件`SetManagedHandler`傳回 E_NOINTERFACE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="abafa-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abafa-110">需求</span><span class="sxs-lookup"><span data-stu-id="abafa-110">Requirements</span></span>  
 <span data-ttu-id="abafa-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abafa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abafa-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abafa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abafa-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abafa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abafa-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abafa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abafa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abafa-115">See also</span></span>

- [<span data-ttu-id="abafa-116">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="abafa-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
