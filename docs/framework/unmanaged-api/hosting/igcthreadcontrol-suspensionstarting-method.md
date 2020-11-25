---
title: IGCThreadControl::SuspensionStarting 方法
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 9d39ee79f7734f7dd099a07640ecb06f4f8dcbb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721656"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="a26cd-102">IGCThreadControl::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="a26cd-102">IGCThreadControl::SuspensionStarting Method</span></span>

<span data-ttu-id="a26cd-103">通知主機執行時間正在等待垃圾收集或其他暫止的執行緒暫停。</span><span class="sxs-lookup"><span data-stu-id="a26cd-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="a26cd-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a26cd-105">備註</span><span class="sxs-lookup"><span data-stu-id="a26cd-105">Remarks</span></span>  

 <span data-ttu-id="a26cd-106">請勿在回呼期間重新排程任何執行緒 `SuspensionStarting` 。</span><span class="sxs-lookup"><span data-stu-id="a26cd-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a26cd-107">需求</span><span class="sxs-lookup"><span data-stu-id="a26cd-107">Requirements</span></span>  

 <span data-ttu-id="a26cd-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a26cd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26cd-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a26cd-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a26cd-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a26cd-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a26cd-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26cd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a26cd-112">See also</span></span>

- [<span data-ttu-id="a26cd-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="a26cd-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
