---
title: ICorDebug::SetUnmanagedHandler 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134052"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="aa2e5-102">ICorDebug::SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="aa2e5-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="aa2e5-103">指定非受控事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="aa2e5-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa2e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa2e5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa2e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="aa2e5-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="aa2e5-106">在[ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)物件的指標，表示非受控事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="aa2e5-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa2e5-107">備註</span><span class="sxs-lookup"><span data-stu-id="aa2e5-107">Remarks</span></span>  
 <span data-ttu-id="aa2e5-108">非受控事件的事件處理常式物件必須在呼叫[ICorDebug：： Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)之後，以及對[ICorDebug：： CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)或[ICorDebug：:D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)的任何呼叫之後設定。</span><span class="sxs-lookup"><span data-stu-id="aa2e5-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="aa2e5-109">不過，基於舊版目的，您不需要設定非受控事件的事件處理常式物件，直到引發第一個原生的 debug 事件為止。</span><span class="sxs-lookup"><span data-stu-id="aa2e5-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="aa2e5-110">具體而言，如果 `ICorDebug::CreateProcess` 已設定 CREATE_SUSPENDED 旗標，則原生 debug 事件必須等到主執行緒繼續執行後才會分派。</span><span class="sxs-lookup"><span data-stu-id="aa2e5-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa2e5-111">需求</span><span class="sxs-lookup"><span data-stu-id="aa2e5-111">Requirements</span></span>  
 <span data-ttu-id="aa2e5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa2e5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa2e5-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa2e5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa2e5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa2e5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa2e5-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa2e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2e5-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa2e5-116">See also</span></span>

- [<span data-ttu-id="aa2e5-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="aa2e5-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
