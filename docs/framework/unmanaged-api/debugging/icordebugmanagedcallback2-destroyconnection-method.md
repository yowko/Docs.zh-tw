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
ms.openlocfilehash: a3093f33f2220b22b7b4b373f6d79a341abf8c9c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501933"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="38a26-102">ICorDebugManagedCallback2::DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="38a26-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="38a26-103">通知偵錯工具已終止指定的連接。</span><span class="sxs-lookup"><span data-stu-id="38a26-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a26-104">語法</span><span class="sxs-lookup"><span data-stu-id="38a26-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38a26-105">參數</span><span class="sxs-lookup"><span data-stu-id="38a26-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="38a26-106">在ICorDebugProcess 物件的指標，表示包含已終結之連接的進程。</span><span class="sxs-lookup"><span data-stu-id="38a26-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="38a26-107">在已損毀之連接的識別碼。</span><span class="sxs-lookup"><span data-stu-id="38a26-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38a26-108">備註</span><span class="sxs-lookup"><span data-stu-id="38a26-108">Remarks</span></span>  
 <span data-ttu-id="38a26-109">`DestroyConnection`當主機呼叫[裝載 API](../hosting/index.md)中的[ICLRDebugManager：： EndConnection](../hosting/iclrdebugmanager-endconnection-method.md)時，將會引發回呼。</span><span class="sxs-lookup"><span data-stu-id="38a26-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a26-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="38a26-110">Requirements</span></span>  
 <span data-ttu-id="38a26-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38a26-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a26-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38a26-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38a26-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38a26-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38a26-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a26-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a26-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38a26-115">See also</span></span>

- [<span data-ttu-id="38a26-116">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="38a26-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="38a26-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="38a26-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
