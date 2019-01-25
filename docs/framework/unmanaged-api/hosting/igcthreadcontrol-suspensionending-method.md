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
ms.openlocfilehash: d77380e35d8f5eee1e50b1030493e0b17cbadfba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713284"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="011a3-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="011a3-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="011a3-103">主應用程式執行階段會進行記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="011a3-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="011a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="011a3-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="011a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="011a3-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="011a3-106">[in]對其執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="011a3-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="011a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="011a3-107">Remarks</span></span>  
 <span data-ttu-id="011a3-108">請勿重新排程在任何執行緒`SuspensionEnding`回呼。</span><span class="sxs-lookup"><span data-stu-id="011a3-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="011a3-109">需求</span><span class="sxs-lookup"><span data-stu-id="011a3-109">Requirements</span></span>  
 <span data-ttu-id="011a3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="011a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="011a3-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="011a3-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="011a3-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="011a3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="011a3-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="011a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011a3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="011a3-114">See also</span></span>
- [<span data-ttu-id="011a3-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="011a3-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
