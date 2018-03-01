---
title: "IGCThreadControl::ThreadIsBlockingForSuspension 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cb7cfbab18334f1892c24225311160179920f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="82265-102">IGCThreadControl::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="82265-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="82265-103">通知主機進行呼叫的執行緒即將封鎖，可能是記憶體回收集合或其他暫止。</span><span class="sxs-lookup"><span data-stu-id="82265-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82265-104">語法</span><span class="sxs-lookup"><span data-stu-id="82265-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="82265-105">備註</span><span class="sxs-lookup"><span data-stu-id="82265-105">Remarks</span></span>  
 <span data-ttu-id="82265-106">主機可以選擇在`ThreadIsBlockingForSuspension`回呼是否要重新排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="82265-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82265-107">需求</span><span class="sxs-lookup"><span data-stu-id="82265-107">Requirements</span></span>  
 <span data-ttu-id="82265-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82265-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82265-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82265-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82265-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="82265-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82265-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82265-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82265-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="82265-112">See Also</span></span>  
 [<span data-ttu-id="82265-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="82265-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
