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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501920"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="3c200-102">ICorDebugManagedCallback2::CreateConnection 方法</span><span class="sxs-lookup"><span data-stu-id="3c200-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="3c200-103">通知偵錯工具已建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="3c200-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c200-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c200-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c200-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c200-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="3c200-106">在"ICorDebugProcess" 物件的指標，代表建立連線的進程。</span><span class="sxs-lookup"><span data-stu-id="3c200-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="3c200-107">在新連接的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3c200-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="3c200-108">在新連接名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="3c200-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c200-109">備註</span><span class="sxs-lookup"><span data-stu-id="3c200-109">Remarks</span></span>  
 <span data-ttu-id="3c200-110">`CreateConnection`在下列任一情況下，將會引發回呼：</span><span class="sxs-lookup"><span data-stu-id="3c200-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="3c200-111">當偵錯工具附加至包含連接的進程時。</span><span class="sxs-lookup"><span data-stu-id="3c200-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="3c200-112">在此情況下，執行時間會 `CreateConnection` 針對進程中的每個連接產生並分派事件和[ICorDebugManagedCallback2：： ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md)事件。</span><span class="sxs-lookup"><span data-stu-id="3c200-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="3c200-113">當主機在[裝載 API](../hosting/index.md)中呼叫[ICLRDebugManager：： BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md)時。</span><span class="sxs-lookup"><span data-stu-id="3c200-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c200-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="3c200-114">Requirements</span></span>  
 <span data-ttu-id="3c200-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c200-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c200-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c200-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c200-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c200-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c200-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c200-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c200-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c200-119">See also</span></span>

- [<span data-ttu-id="3c200-120">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="3c200-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="3c200-121">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3c200-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
