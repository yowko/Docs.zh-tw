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
ms.openlocfilehash: 97a4a464d3dfb7b333f44ac4206bd880fd171e16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723411"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="9eb53-102">ICorDebug::SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="9eb53-102">ICorDebug::SetManagedHandler Method</span></span>

<span data-ttu-id="9eb53-103">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="9eb53-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb53-104">語法</span><span class="sxs-lookup"><span data-stu-id="9eb53-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eb53-105">參數</span><span class="sxs-lookup"><span data-stu-id="9eb53-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="9eb53-106">在 [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) 物件的指標，也就是事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="9eb53-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eb53-107">備註</span><span class="sxs-lookup"><span data-stu-id="9eb53-107">Remarks</span></span>  

 <span data-ttu-id="9eb53-108">`SetManagedHandler` 必須在建立時呼叫。</span><span class="sxs-lookup"><span data-stu-id="9eb53-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="9eb53-109">如果 `ICorDebugManagedCallback` 執行不包含足夠的介面來處理正在進行偵錯工具的偵錯工具，就會傳回 `SetManagedHandler` E_NOINTERFACE 的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9eb53-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eb53-110">需求</span><span class="sxs-lookup"><span data-stu-id="9eb53-110">Requirements</span></span>  

 <span data-ttu-id="9eb53-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9eb53-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eb53-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9eb53-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eb53-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eb53-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eb53-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eb53-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb53-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eb53-115">See also</span></span>

- [<span data-ttu-id="9eb53-116">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="9eb53-116">ICorDebug Interface</span></span>](icordebug-interface.md)
