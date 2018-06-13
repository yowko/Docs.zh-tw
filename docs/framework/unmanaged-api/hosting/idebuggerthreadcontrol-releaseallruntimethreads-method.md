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
ms.openlocfilehash: 5b3623c886a48cc938be017f955fbdac1df3f10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437631"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="384fd-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="384fd-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="384fd-103">通知主機有偵錯服務即將要釋放所有的執行緒所封鎖。</span><span class="sxs-lookup"><span data-stu-id="384fd-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="384fd-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="384fd-105">備註</span><span class="sxs-lookup"><span data-stu-id="384fd-105">Remarks</span></span>  
 <span data-ttu-id="384fd-106">`ReleaseAllRuntimeThreads`絕不會在執行階段執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="384fd-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="384fd-107">如果主機已封鎖在執行階段執行緒，則它應該立即放開。</span><span class="sxs-lookup"><span data-stu-id="384fd-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="384fd-108">需求</span><span class="sxs-lookup"><span data-stu-id="384fd-108">Requirements</span></span>  
 <span data-ttu-id="384fd-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="384fd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="384fd-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="384fd-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="384fd-111">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="384fd-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="384fd-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="384fd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384fd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="384fd-113">See Also</span></span>  
 [<span data-ttu-id="384fd-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="384fd-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
