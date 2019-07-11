---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09895294c4678cdb1dd033076cfb42853aa06b2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780494"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="eb1f1-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="eb1f1-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="eb1f1-103">主應用程式的偵錯的服務是即將要釋放所有封鎖的執行緒。</span><span class="sxs-lookup"><span data-stu-id="eb1f1-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb1f1-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb1f1-105">備註</span><span class="sxs-lookup"><span data-stu-id="eb1f1-105">Remarks</span></span>  
 <span data-ttu-id="eb1f1-106">`ReleaseAllRuntimeThreads`絕不會在執行階段的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="eb1f1-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="eb1f1-107">如果主機有執行階段的執行緒封鎖，它應該立即釋放。</span><span class="sxs-lookup"><span data-stu-id="eb1f1-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb1f1-108">需求</span><span class="sxs-lookup"><span data-stu-id="eb1f1-108">Requirements</span></span>  
 <span data-ttu-id="eb1f1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb1f1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb1f1-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb1f1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb1f1-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eb1f1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb1f1-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb1f1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1f1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb1f1-113">See also</span></span>

- [<span data-ttu-id="eb1f1-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="eb1f1-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
