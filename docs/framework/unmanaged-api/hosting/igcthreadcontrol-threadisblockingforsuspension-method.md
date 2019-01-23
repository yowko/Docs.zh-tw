---
title: IGCThreadControl::ThreadIsBlockingForSuspension 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa2872fec7765f38fba9589a6fab659e73131937
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620457"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="5fbdc-102">IGCThreadControl::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="5fbdc-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="5fbdc-103">主應用程式正在進行呼叫的執行緒即將封鎖，可能是記憶體回收或其他暫止。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fbdc-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fbdc-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="5fbdc-105">備註</span><span class="sxs-lookup"><span data-stu-id="5fbdc-105">Remarks</span></span>  
 <span data-ttu-id="5fbdc-106">主機可以選擇在`ThreadIsBlockingForSuspension`回呼是否要重新排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fbdc-107">需求</span><span class="sxs-lookup"><span data-stu-id="5fbdc-107">Requirements</span></span>  
 <span data-ttu-id="5fbdc-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fbdc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fbdc-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5fbdc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5fbdc-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5fbdc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fbdc-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fbdc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fbdc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fbdc-112">See also</span></span>
- [<span data-ttu-id="5fbdc-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="5fbdc-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
