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
ms.openlocfilehash: 90b0cba50129bc728089e41ece5a30697cfc3bc5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144413"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="39358-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="39358-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="39358-103">主應用程式執行階段會進行記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="39358-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39358-104">語法</span><span class="sxs-lookup"><span data-stu-id="39358-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39358-105">參數</span><span class="sxs-lookup"><span data-stu-id="39358-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="39358-106">[in]對其執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="39358-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39358-107">備註</span><span class="sxs-lookup"><span data-stu-id="39358-107">Remarks</span></span>  
 <span data-ttu-id="39358-108">請勿重新排程在任何執行緒`SuspensionEnding`回呼。</span><span class="sxs-lookup"><span data-stu-id="39358-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39358-109">需求</span><span class="sxs-lookup"><span data-stu-id="39358-109">Requirements</span></span>  
 <span data-ttu-id="39358-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39358-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39358-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39358-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39358-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="39358-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="39358-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="39358-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="39358-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39358-114">See also</span></span>

- [<span data-ttu-id="39358-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="39358-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
