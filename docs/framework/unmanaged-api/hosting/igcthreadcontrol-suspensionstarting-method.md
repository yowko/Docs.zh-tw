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
ms.openlocfilehash: 2acabe66e3b6b5652df20e31a9d2294c2396b54b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805104"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="bc795-102">IGCThreadControl::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="bc795-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="bc795-103">通知主機執行時間正在中止垃圾收集或其他暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="bc795-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc795-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc795-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="bc795-105">備註</span><span class="sxs-lookup"><span data-stu-id="bc795-105">Remarks</span></span>  
 <span data-ttu-id="bc795-106">請勿在回呼期間重新排定任何執行緒 `SuspensionStarting` 。</span><span class="sxs-lookup"><span data-stu-id="bc795-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc795-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="bc795-107">Requirements</span></span>  
 <span data-ttu-id="bc795-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc795-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc795-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="bc795-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc795-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bc795-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc795-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc795-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc795-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc795-112">See also</span></span>

- [<span data-ttu-id="bc795-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="bc795-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
