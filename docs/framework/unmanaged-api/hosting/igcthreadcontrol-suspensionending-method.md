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
ms.openlocfilehash: 8300daf0d39745ceda80f6c56da7e3c459a97468
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805109"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="a7bd4-102">IGCThreadControl::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="a7bd4-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="a7bd4-103">通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。</span><span class="sxs-lookup"><span data-stu-id="a7bd4-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7bd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7bd4-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7bd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7bd4-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="a7bd4-106">在已執行垃圾收集的世代。</span><span class="sxs-lookup"><span data-stu-id="a7bd4-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7bd4-107">備註</span><span class="sxs-lookup"><span data-stu-id="a7bd4-107">Remarks</span></span>  
 <span data-ttu-id="a7bd4-108">請勿在回呼期間重新排定任何執行緒 `SuspensionEnding` 。</span><span class="sxs-lookup"><span data-stu-id="a7bd4-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7bd4-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="a7bd4-109">Requirements</span></span>  
 <span data-ttu-id="a7bd4-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7bd4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7bd4-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a7bd4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7bd4-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7bd4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7bd4-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7bd4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7bd4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7bd4-114">See also</span></span>

- [<span data-ttu-id="a7bd4-115">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="a7bd4-115">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
