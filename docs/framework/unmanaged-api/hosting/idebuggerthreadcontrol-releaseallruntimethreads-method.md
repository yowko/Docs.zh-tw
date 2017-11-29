---
title: "IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a087dbcff961ca1ac1cf03d30fdc336ec9ca0515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="3f74c-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="3f74c-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="3f74c-103">通知主機有偵錯服務即將要釋放所有的執行緒所封鎖。</span><span class="sxs-lookup"><span data-stu-id="3f74c-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f74c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f74c-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f74c-105">備註</span><span class="sxs-lookup"><span data-stu-id="3f74c-105">Remarks</span></span>  
 <span data-ttu-id="3f74c-106">`ReleaseAllRuntimeThreads`絕不會在執行階段執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="3f74c-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="3f74c-107">如果主機已封鎖在執行階段執行緒，則它應該立即放開。</span><span class="sxs-lookup"><span data-stu-id="3f74c-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f74c-108">需求</span><span class="sxs-lookup"><span data-stu-id="3f74c-108">Requirements</span></span>  
 <span data-ttu-id="3f74c-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f74c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f74c-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f74c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f74c-111">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3f74c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f74c-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f74c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f74c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f74c-113">See Also</span></span>  
 [<span data-ttu-id="3f74c-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="3f74c-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
