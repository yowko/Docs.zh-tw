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
ms.openlocfilehash: 50ffb33456f942a71089f9bc44daa07f6b77ab21
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805292"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="6276c-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="6276c-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="6276c-103">通知主機偵錯工具即將釋放所有封鎖的執行緒。</span><span class="sxs-lookup"><span data-stu-id="6276c-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6276c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6276c-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="6276c-105">備註</span><span class="sxs-lookup"><span data-stu-id="6276c-105">Remarks</span></span>  
 <span data-ttu-id="6276c-106">`ReleaseAllRuntimeThreads`永遠不會在運行時間表程上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="6276c-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="6276c-107">如果主機已封鎖運行時間表程，它就應該立即發行。</span><span class="sxs-lookup"><span data-stu-id="6276c-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6276c-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="6276c-108">Requirements</span></span>  
 <span data-ttu-id="6276c-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6276c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6276c-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6276c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6276c-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6276c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6276c-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6276c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6276c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6276c-113">See also</span></span>

- [<span data-ttu-id="6276c-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="6276c-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
