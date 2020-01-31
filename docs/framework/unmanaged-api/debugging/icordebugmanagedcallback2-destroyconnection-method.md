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
ms.openlocfilehash: 4f6940f863504a9aedd9539e121c7b3791f746b9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788312"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="effaf-102">ICorDebugManagedCallback2::DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="effaf-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="effaf-103">通知偵錯工具已終止指定的連接。</span><span class="sxs-lookup"><span data-stu-id="effaf-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="effaf-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="effaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="effaf-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="effaf-106">在ICorDebugProcess 物件的指標，表示包含已終結之連接的進程。</span><span class="sxs-lookup"><span data-stu-id="effaf-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="effaf-107">在已損毀之連接的識別碼。</span><span class="sxs-lookup"><span data-stu-id="effaf-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="effaf-108">備註</span><span class="sxs-lookup"><span data-stu-id="effaf-108">Remarks</span></span>  
 <span data-ttu-id="effaf-109">當主機呼叫[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)中的[ICLRDebugManager：： EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)時，將會引發 `DestroyConnection` 回呼。</span><span class="sxs-lookup"><span data-stu-id="effaf-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="effaf-110">需求</span><span class="sxs-lookup"><span data-stu-id="effaf-110">Requirements</span></span>  
 <span data-ttu-id="effaf-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="effaf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="effaf-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="effaf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="effaf-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="effaf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="effaf-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="effaf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effaf-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="effaf-115">See also</span></span>

- [<span data-ttu-id="effaf-116">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="effaf-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="effaf-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="effaf-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
