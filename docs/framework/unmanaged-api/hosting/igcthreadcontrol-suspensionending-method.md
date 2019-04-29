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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763200"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="c5437-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="c5437-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="c5437-103">主應用程式執行階段會進行記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="c5437-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5437-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5437-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5437-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5437-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="c5437-106">[in]對其執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="c5437-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5437-107">備註</span><span class="sxs-lookup"><span data-stu-id="c5437-107">Remarks</span></span>  
 <span data-ttu-id="c5437-108">請勿重新排程在任何執行緒`SuspensionEnding`回呼。</span><span class="sxs-lookup"><span data-stu-id="c5437-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5437-109">需求</span><span class="sxs-lookup"><span data-stu-id="c5437-109">Requirements</span></span>  
 <span data-ttu-id="c5437-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5437-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5437-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5437-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5437-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c5437-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5437-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5437-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5437-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5437-114">See also</span></span>

- [<span data-ttu-id="c5437-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="c5437-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
