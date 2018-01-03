---
title: "IGCThreadControl::SuspensionEnding 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d17d9d2d676b83c21bea46e47914fecbec9ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="f232c-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="f232c-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="f232c-103">通知主機執行階段會在記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="f232c-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f232c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f232c-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f232c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f232c-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="f232c-106">[in]其執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="f232c-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f232c-107">備註</span><span class="sxs-lookup"><span data-stu-id="f232c-107">Remarks</span></span>  
 <span data-ttu-id="f232c-108">請勿重新排程期間的任何執行緒`SuspensionEnding`回呼。</span><span class="sxs-lookup"><span data-stu-id="f232c-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f232c-109">需求</span><span class="sxs-lookup"><span data-stu-id="f232c-109">Requirements</span></span>  
 <span data-ttu-id="f232c-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f232c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f232c-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f232c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f232c-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f232c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f232c-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f232c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f232c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f232c-114">See Also</span></span>  
 [<span data-ttu-id="f232c-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="f232c-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
