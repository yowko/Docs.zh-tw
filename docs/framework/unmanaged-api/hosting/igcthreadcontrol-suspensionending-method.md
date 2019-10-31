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
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134788"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="3da61-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="3da61-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="3da61-103">通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。</span><span class="sxs-lookup"><span data-stu-id="3da61-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da61-104">語法</span><span class="sxs-lookup"><span data-stu-id="3da61-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3da61-105">參數</span><span class="sxs-lookup"><span data-stu-id="3da61-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="3da61-106">在已執行垃圾收集的世代。</span><span class="sxs-lookup"><span data-stu-id="3da61-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3da61-107">備註</span><span class="sxs-lookup"><span data-stu-id="3da61-107">Remarks</span></span>  
 <span data-ttu-id="3da61-108">請勿在 `SuspensionEnding` 回呼期間重新排定任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="3da61-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da61-109">需求</span><span class="sxs-lookup"><span data-stu-id="3da61-109">Requirements</span></span>  
 <span data-ttu-id="3da61-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3da61-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da61-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3da61-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3da61-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3da61-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3da61-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da61-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da61-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3da61-114">See also</span></span>

- [<span data-ttu-id="3da61-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="3da61-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
