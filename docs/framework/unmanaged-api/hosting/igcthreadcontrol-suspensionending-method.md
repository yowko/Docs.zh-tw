---
title: IGCThreadControl::SuspensionEnding 方法
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffee1550c64f1ce7c438580ce78a497aeeb99f3a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468763"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="fda30-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="fda30-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="fda30-103">主應用程式執行階段會進行記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="fda30-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda30-104">語法</span><span class="sxs-lookup"><span data-stu-id="fda30-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fda30-105">參數</span><span class="sxs-lookup"><span data-stu-id="fda30-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="fda30-106">[in]對其執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="fda30-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fda30-107">備註</span><span class="sxs-lookup"><span data-stu-id="fda30-107">Remarks</span></span>  
 <span data-ttu-id="fda30-108">請勿重新排程在任何執行緒`SuspensionEnding`回呼。</span><span class="sxs-lookup"><span data-stu-id="fda30-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fda30-109">需求</span><span class="sxs-lookup"><span data-stu-id="fda30-109">Requirements</span></span>  
 <span data-ttu-id="fda30-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fda30-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fda30-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fda30-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fda30-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fda30-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fda30-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fda30-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda30-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fda30-114">See also</span></span>
- [<span data-ttu-id="fda30-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="fda30-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
