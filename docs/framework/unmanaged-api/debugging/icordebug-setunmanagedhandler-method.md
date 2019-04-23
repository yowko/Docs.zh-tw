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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c234b3953130f53d7e6b583cd92670149a70689b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168855"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="e7c12-102">ICorDebug::SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="e7c12-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="e7c12-103">指定未受管理的事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="e7c12-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c12-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7c12-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7c12-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7c12-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="e7c12-106">[in]指標[ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)物件，表示 unmanaged 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e7c12-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7c12-107">備註</span><span class="sxs-lookup"><span data-stu-id="e7c12-107">Remarks</span></span>  
 <span data-ttu-id="e7c12-108">事件處理常式物件的非受控事件必須在呼叫之後設定[icordebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)以及任何呼叫之前[icordebug:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)或[icordebug:: Debugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="e7c12-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="e7c12-109">不過，基於舊版時，您不需要設定未受管理的事件，直到第一個原生偵錯事件引發的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="e7c12-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="e7c12-110">具體來說，如果`ICorDebug::CreateProcess`設定 CREATE_SUSPENDED 旗標，不可分派的事件，直到主執行緒繼續執行的原生偵錯。</span><span class="sxs-lookup"><span data-stu-id="e7c12-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c12-111">需求</span><span class="sxs-lookup"><span data-stu-id="e7c12-111">Requirements</span></span>  
 <span data-ttu-id="e7c12-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7c12-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c12-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7c12-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7c12-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7c12-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7c12-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7c12-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c12-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7c12-116">See also</span></span>

- [<span data-ttu-id="e7c12-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="e7c12-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
