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
ms.openlocfilehash: d0986645a8ce4076c27f39f2ae8004ef20bb4bdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437748"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="9676f-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="9676f-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="9676f-103">通知主機執行階段會在記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="9676f-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9676f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9676f-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9676f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9676f-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="9676f-106">[in]其執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="9676f-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9676f-107">備註</span><span class="sxs-lookup"><span data-stu-id="9676f-107">Remarks</span></span>  
 <span data-ttu-id="9676f-108">請勿重新排程期間的任何執行緒`SuspensionEnding`回呼。</span><span class="sxs-lookup"><span data-stu-id="9676f-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9676f-109">需求</span><span class="sxs-lookup"><span data-stu-id="9676f-109">Requirements</span></span>  
 <span data-ttu-id="9676f-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9676f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9676f-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9676f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9676f-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9676f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9676f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9676f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9676f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9676f-114">See Also</span></span>  
 [<span data-ttu-id="9676f-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="9676f-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
