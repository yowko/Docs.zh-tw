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
ms.openlocfilehash: 4638672b1d64a9ea07618212cc514d00996470eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721669"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="45014-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="45014-102">IGCThreadControl::SuspensionEnding Method</span></span>

<span data-ttu-id="45014-103">通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。</span><span class="sxs-lookup"><span data-stu-id="45014-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45014-104">語法</span><span class="sxs-lookup"><span data-stu-id="45014-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45014-105">參數</span><span class="sxs-lookup"><span data-stu-id="45014-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="45014-106">在已執行垃圾收集的產生。</span><span class="sxs-lookup"><span data-stu-id="45014-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45014-107">備註</span><span class="sxs-lookup"><span data-stu-id="45014-107">Remarks</span></span>  

 <span data-ttu-id="45014-108">請勿在回呼期間重新排程任何執行緒 `SuspensionEnding` 。</span><span class="sxs-lookup"><span data-stu-id="45014-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45014-109">需求</span><span class="sxs-lookup"><span data-stu-id="45014-109">Requirements</span></span>  

 <span data-ttu-id="45014-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45014-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45014-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="45014-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45014-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="45014-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45014-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45014-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45014-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45014-114">See also</span></span>

- [<span data-ttu-id="45014-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="45014-115">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
