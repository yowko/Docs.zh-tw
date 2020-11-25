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
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723385"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="bb5a0-102">ICorDebug::SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="bb5a0-102">ICorDebug::SetUnmanagedHandler Method</span></span>

<span data-ttu-id="bb5a0-103">指定非受控事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="bb5a0-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb5a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb5a0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb5a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb5a0-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="bb5a0-106">在 [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) 物件的指標，該物件代表非受控事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bb5a0-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb5a0-107">備註</span><span class="sxs-lookup"><span data-stu-id="bb5a0-107">Remarks</span></span>  

 <span data-ttu-id="bb5a0-108">您必須在呼叫 [ICorDebug：： Initialize](icordebug-initialize-method.md) 之後，以及對 [ICorDebug：： CreateProcess](icordebug-createprocess-method.md) 或 [ICorDebug：:D ebugactiveprocess](icordebug-debugactiveprocess-method.md)的任何呼叫之前，設定非受控事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="bb5a0-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="bb5a0-109">不過，基於舊版的目的，在引發第一個原生偵錯工具事件之前，您不需要為非受控事件設定事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="bb5a0-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="bb5a0-110">具體而言，如果 `ICorDebug::CreateProcess` 已設定 CREATE_SUSPENDED 旗標，則在繼續主執行緒之前，無法分派原生偵錯工具事件。</span><span class="sxs-lookup"><span data-stu-id="bb5a0-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb5a0-111">需求</span><span class="sxs-lookup"><span data-stu-id="bb5a0-111">Requirements</span></span>  

 <span data-ttu-id="bb5a0-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb5a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb5a0-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb5a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb5a0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb5a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb5a0-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb5a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5a0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb5a0-116">See also</span></span>

- [<span data-ttu-id="bb5a0-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="bb5a0-117">ICorDebug Interface</span></span>](icordebug-interface.md)
