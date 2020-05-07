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
ms.openlocfilehash: 7c3251b2cf7a4d0d97df0e6ecc9b332e3ed8e500
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895332"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="690ac-102">ICorDebug::SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="690ac-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="690ac-103">指定非受控事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="690ac-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="690ac-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="690ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="690ac-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="690ac-106">在[ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)物件的指標，表示非受控事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="690ac-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="690ac-107">備註</span><span class="sxs-lookup"><span data-stu-id="690ac-107">Remarks</span></span>  
 <span data-ttu-id="690ac-108">非受控事件的事件處理常式物件必須在呼叫[ICorDebug：： Initialize](icordebug-initialize-method.md)之後，以及對[ICorDebug：： CreateProcess](icordebug-createprocess-method.md)或[ICorDebug：:D ebugactiveprocess](icordebug-debugactiveprocess-method.md)的任何呼叫之後設定。</span><span class="sxs-lookup"><span data-stu-id="690ac-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="690ac-109">不過，基於舊版目的，您不需要設定非受控事件的事件處理常式物件，直到引發第一個原生的 debug 事件為止。</span><span class="sxs-lookup"><span data-stu-id="690ac-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="690ac-110">具體而言， `ICorDebug::CreateProcess`如果已設定 CREATE_SUSPENDED 旗標，則原生 debug 事件無法分派到主執行緒繼續執行。</span><span class="sxs-lookup"><span data-stu-id="690ac-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="690ac-111">需求</span><span class="sxs-lookup"><span data-stu-id="690ac-111">Requirements</span></span>  
 <span data-ttu-id="690ac-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="690ac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="690ac-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="690ac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="690ac-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="690ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="690ac-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="690ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690ac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="690ac-116">See also</span></span>

- [<span data-ttu-id="690ac-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="690ac-117">ICorDebug Interface</span></span>](icordebug-interface.md)
