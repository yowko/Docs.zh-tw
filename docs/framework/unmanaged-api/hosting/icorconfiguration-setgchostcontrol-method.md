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
ms.openlocfilehash: a64922e1fe069d682f7ebc51040d06231a8b49c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484351"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="bb3a8-102">ICorConfiguration::SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="bb3a8-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="bb3a8-103">設定要求的主機，若要變更虛擬記憶體的限制，記憶體回收行程所使用的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="bb3a8-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb3a8-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb3a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb3a8-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="bb3a8-106">[in]指標[IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)物件，可讓記憶體回收行程，以要求主機若要變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="bb3a8-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3a8-107">需求</span><span class="sxs-lookup"><span data-stu-id="bb3a8-107">Requirements</span></span>  
 <span data-ttu-id="bb3a8-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb3a8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3a8-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb3a8-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb3a8-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bb3a8-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb3a8-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3a8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3a8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb3a8-112">See also</span></span>
- [<span data-ttu-id="bb3a8-113">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="bb3a8-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
