---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 490648ab8883b1dba257b82c0d0fa3c8e4783814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684157"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="d9a98-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="d9a98-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="d9a98-103">通知主機偵錯工具即將釋放封鎖的所有線程。</span><span class="sxs-lookup"><span data-stu-id="d9a98-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a98-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9a98-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9a98-105">備註</span><span class="sxs-lookup"><span data-stu-id="d9a98-105">Remarks</span></span>  

 <span data-ttu-id="d9a98-106">`ReleaseAllRuntimeThreads`永遠不會在運行時間表程上呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="d9a98-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="d9a98-107">如果主機已封鎖運行時間表程，則應該立即釋出。</span><span class="sxs-lookup"><span data-stu-id="d9a98-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9a98-108">需求</span><span class="sxs-lookup"><span data-stu-id="d9a98-108">Requirements</span></span>  

 <span data-ttu-id="d9a98-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9a98-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9a98-110">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d9a98-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9a98-111">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d9a98-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9a98-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9a98-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a98-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9a98-113">See also</span></span>

- [<span data-ttu-id="d9a98-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="d9a98-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
