---
title: ICorDebugManagedCallback2::CreateConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7024b8c0682b3351d185e518dd149737beb04bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416354"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="6e18b-102">ICorDebugManagedCallback2::CreateConnection 方法</span><span class="sxs-lookup"><span data-stu-id="6e18b-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="6e18b-103">告知偵錯工具已建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="6e18b-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e18b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e18b-104">Syntax</span></span>  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e18b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e18b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="6e18b-106">[in]代表程序的連接原先建立"ICorDebugProcess 」 物件的指標</span><span class="sxs-lookup"><span data-stu-id="6e18b-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="6e18b-107">[in]新的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="6e18b-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="6e18b-108">[in]新連接的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="6e18b-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e18b-109">備註</span><span class="sxs-lookup"><span data-stu-id="6e18b-109">Remarks</span></span>  
 <span data-ttu-id="6e18b-110">A`CreateConnection`回呼將會引發在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="6e18b-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="6e18b-111">當偵錯工具附加至處理序，包含連線。</span><span class="sxs-lookup"><span data-stu-id="6e18b-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="6e18b-112">在此情況下，執行階段將會產生並分派`CreateConnection`事件和[icordebugmanagedcallback2:: Changeconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)程序中每個連接的事件。</span><span class="sxs-lookup"><span data-stu-id="6e18b-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
-   <span data-ttu-id="6e18b-113">當主機呼叫[iclrdebugmanager:: Beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6e18b-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e18b-114">需求</span><span class="sxs-lookup"><span data-stu-id="6e18b-114">Requirements</span></span>  
 <span data-ttu-id="6e18b-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e18b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e18b-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e18b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e18b-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e18b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e18b-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e18b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e18b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e18b-119">See Also</span></span>  
 [<span data-ttu-id="6e18b-120">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="6e18b-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="6e18b-121">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6e18b-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
