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
ms.openlocfilehash: 35ae3a9761798ed9ea42b984f2c6c2cad4e42777
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704098"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="11b03-102">ICorDebugManagedCallback2::DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="11b03-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="11b03-103">指定的連接已終止會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="11b03-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b03-104">語法</span><span class="sxs-lookup"><span data-stu-id="11b03-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11b03-105">參數</span><span class="sxs-lookup"><span data-stu-id="11b03-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="11b03-106">[in]代表包含已被終結的連接程序 ICorDebugProcess 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="11b03-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="11b03-107">[in]已被終結之連線識別碼。</span><span class="sxs-lookup"><span data-stu-id="11b03-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11b03-108">備註</span><span class="sxs-lookup"><span data-stu-id="11b03-108">Remarks</span></span>  
 <span data-ttu-id="11b03-109">A`DestroyConnection`時，主機會呼叫會引發回呼[iclrdebugmanager:: Endconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="11b03-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11b03-110">需求</span><span class="sxs-lookup"><span data-stu-id="11b03-110">Requirements</span></span>  
 <span data-ttu-id="11b03-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11b03-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b03-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11b03-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11b03-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11b03-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11b03-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b03-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11b03-115">See also</span></span>

- [<span data-ttu-id="11b03-116">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="11b03-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="11b03-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="11b03-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
