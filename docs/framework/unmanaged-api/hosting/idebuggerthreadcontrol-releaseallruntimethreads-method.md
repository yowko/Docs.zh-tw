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
ms.openlocfilehash: 136dab5c05c310d85a5e18bcdc6da0de901d3ace
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227466"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="b502d-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b502d-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="b502d-103">主應用程式的偵錯的服務是即將要釋放所有封鎖的執行緒。</span><span class="sxs-lookup"><span data-stu-id="b502d-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b502d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b502d-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b502d-105">備註</span><span class="sxs-lookup"><span data-stu-id="b502d-105">Remarks</span></span>  
 <span data-ttu-id="b502d-106">`ReleaseAllRuntimeThreads`絕不會在執行階段的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b502d-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="b502d-107">如果主機有執行階段的執行緒封鎖，它應該立即釋放。</span><span class="sxs-lookup"><span data-stu-id="b502d-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b502d-108">需求</span><span class="sxs-lookup"><span data-stu-id="b502d-108">Requirements</span></span>  
 <span data-ttu-id="b502d-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b502d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b502d-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b502d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b502d-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b502d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b502d-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b502d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b502d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b502d-113">See also</span></span>

- [<span data-ttu-id="b502d-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="b502d-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
