---
title: ICorConfiguration::SetGCHostControl 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50a92058e8a394b95c690d19f1bafdddbed8246a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135989"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="3030a-102">ICorConfiguration::SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="3030a-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="3030a-103">設定要求的主機，若要變更虛擬記憶體的限制，記憶體回收行程所使用的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="3030a-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3030a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3030a-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3030a-105">參數</span><span class="sxs-lookup"><span data-stu-id="3030a-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="3030a-106">[in]指標[IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)物件，可讓記憶體回收行程，以要求主機若要變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="3030a-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3030a-107">需求</span><span class="sxs-lookup"><span data-stu-id="3030a-107">Requirements</span></span>  
 <span data-ttu-id="3030a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3030a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3030a-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3030a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3030a-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3030a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3030a-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3030a-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3030a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3030a-112">See also</span></span>

- [<span data-ttu-id="3030a-113">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="3030a-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
