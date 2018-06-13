---
title: ICorDebugManagedCallback2::DestroyConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6d4acb7d1156babbd698201c5aea2810644db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415398"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="9647f-102">ICorDebugManagedCallback2::DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="9647f-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="9647f-103">指定的連接已終止會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="9647f-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9647f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9647f-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9647f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9647f-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="9647f-106">[in]表示包含連接已損毀的程序的 ICorDebugProcess 物件指標。</span><span class="sxs-lookup"><span data-stu-id="9647f-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="9647f-107">[in]已被終結的連線識別碼。</span><span class="sxs-lookup"><span data-stu-id="9647f-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9647f-108">備註</span><span class="sxs-lookup"><span data-stu-id="9647f-108">Remarks</span></span>  
 <span data-ttu-id="9647f-109">A`DestroyConnection`時，主機會呼叫回呼會引發[iclrdebugmanager:: Endconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9647f-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9647f-110">需求</span><span class="sxs-lookup"><span data-stu-id="9647f-110">Requirements</span></span>  
 <span data-ttu-id="9647f-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9647f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9647f-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9647f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9647f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9647f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9647f-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9647f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9647f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9647f-115">See Also</span></span>  
 [<span data-ttu-id="9647f-116">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="9647f-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="9647f-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9647f-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
