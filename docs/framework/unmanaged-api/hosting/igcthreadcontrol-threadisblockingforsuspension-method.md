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
ms.openlocfilehash: b5f6d7d40274972438a01313bc6aaec475b8e0c6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805081"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="707b4-102">IGCThreadControl::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="707b4-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="707b4-103">通知主機正在進行呼叫的執行緒即將封鎖，可能是因為垃圾收集或其他暫停。</span><span class="sxs-lookup"><span data-stu-id="707b4-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="707b4-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="707b4-105">備註</span><span class="sxs-lookup"><span data-stu-id="707b4-105">Remarks</span></span>  
 <span data-ttu-id="707b4-106">主機可以在回呼中選擇 `ThreadIsBlockingForSuspension` 是否要重新排定執行緒。</span><span class="sxs-lookup"><span data-stu-id="707b4-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707b4-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="707b4-107">Requirements</span></span>  
 <span data-ttu-id="707b4-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="707b4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="707b4-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="707b4-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="707b4-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="707b4-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="707b4-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="707b4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707b4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="707b4-112">See also</span></span>

- [<span data-ttu-id="707b4-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="707b4-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
