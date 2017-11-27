---
title: "ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd865e720e4ed938cf1634ebe5f1c324c4c3256e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="c99eb-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法</span><span class="sxs-lookup"><span data-stu-id="c99eb-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>
<span data-ttu-id="c99eb-103">取得目前[icordebugmanagedcallback3:: Customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)目前執行緒上的物件。</span><span class="sxs-lookup"><span data-stu-id="c99eb-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c99eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c99eb-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCustomDebuggerNotification(  
    [out] ICorDebugValue **ppNotificationObject  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c99eb-105">參數</span><span class="sxs-lookup"><span data-stu-id="c99eb-105">Parameters</span></span>  
 `ppNOtificationObject`  
 <span data-ttu-id="c99eb-106">[out]目前的指標`ICorDebugManagedCallback3::CustomNotification`目前執行緒上的物件。</span><span class="sxs-lookup"><span data-stu-id="c99eb-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c99eb-107">備註</span><span class="sxs-lookup"><span data-stu-id="c99eb-107">Remarks</span></span>  
 <span data-ttu-id="c99eb-108">值`ppNotificationObject`為 null，不會從呼叫的方法如果`ICorDebugManagedCallback3::CustomNotification`回呼，或如果目前的通知物件不存在。</span><span class="sxs-lookup"><span data-stu-id="c99eb-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c99eb-109">需求</span><span class="sxs-lookup"><span data-stu-id="c99eb-109">Requirements</span></span>  
 <span data-ttu-id="c99eb-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c99eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c99eb-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c99eb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c99eb-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c99eb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c99eb-113">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c99eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99eb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c99eb-114">See Also</span></span>  
 [<span data-ttu-id="c99eb-115">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="c99eb-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="c99eb-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c99eb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c99eb-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="c99eb-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
