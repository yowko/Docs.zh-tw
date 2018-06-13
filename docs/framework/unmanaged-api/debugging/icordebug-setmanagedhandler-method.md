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
ms.openlocfilehash: bcf97f9fffabb9ae9579016517cfc335e6f783a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404569"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="9182d-102">ICorDebug::SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="9182d-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="9182d-103">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="9182d-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9182d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9182d-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9182d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9182d-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="9182d-106">[in]指標[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)物件，它是事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="9182d-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9182d-107">備註</span><span class="sxs-lookup"><span data-stu-id="9182d-107">Remarks</span></span>  
 <span data-ttu-id="9182d-108">`SetManagedHandler` 必須在建立時呼叫。</span><span class="sxs-lookup"><span data-stu-id="9182d-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="9182d-109">如果`ICorDebugManagedCallback`實作不包含足夠的介面來處理應用程式進行偵錯，偵錯事件`SetManagedHandler`傳回 E_NOINTERFACE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9182d-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9182d-110">需求</span><span class="sxs-lookup"><span data-stu-id="9182d-110">Requirements</span></span>  
 <span data-ttu-id="9182d-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9182d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9182d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9182d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9182d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9182d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9182d-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9182d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9182d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9182d-115">See Also</span></span>  
 [<span data-ttu-id="9182d-116">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="9182d-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
