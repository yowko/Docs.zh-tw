---
title: "ICorDebug::SetUnmanagedHandler 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetUnmanagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 658cbaeb10496ccd88e0abb3d2174289a820c2e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="73496-102">ICorDebug::SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="73496-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="73496-103">指定 unmanaged 事件的事件處理常式的物件。</span><span class="sxs-lookup"><span data-stu-id="73496-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73496-104">語法</span><span class="sxs-lookup"><span data-stu-id="73496-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73496-105">參數</span><span class="sxs-lookup"><span data-stu-id="73496-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="73496-106">[in]指標[ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)物件，表示 unmanaged 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="73496-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73496-107">備註</span><span class="sxs-lookup"><span data-stu-id="73496-107">Remarks</span></span>  
 <span data-ttu-id="73496-108">此事件處理常式物件的 unmanaged 呼叫之後，必須設定事件[icordebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)和任何呼叫之前[icordebug:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)或[icordebug:: Debugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="73496-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="73496-109">不過，舊版的用途，您不必設定未受管理的事件，直到第一個原生偵錯事件就會引發的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="73496-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="73496-110">具體來說，如果`ICorDebug::CreateProcess`已設定 CREATE_SUSPENDED 旗標，不可分派的事件，主執行緒繼續執行之前的原生偵錯。</span><span class="sxs-lookup"><span data-stu-id="73496-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73496-111">需求</span><span class="sxs-lookup"><span data-stu-id="73496-111">Requirements</span></span>  
 <span data-ttu-id="73496-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73496-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73496-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73496-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73496-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73496-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73496-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73496-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73496-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73496-116">See Also</span></span>  
 [<span data-ttu-id="73496-117">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="73496-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
