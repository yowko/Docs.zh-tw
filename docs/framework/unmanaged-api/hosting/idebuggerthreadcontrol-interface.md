---
title: IDebuggerThreadControl 介面
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: a65f9f0f29a43cf3d26b4b2bc5f6f594f0557009
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133165"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="a80bd-102">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="a80bd-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="a80bd-103">提供方法，以通知主機有關偵錯工具的執行緒封鎖和解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="a80bd-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a80bd-104">方法</span><span class="sxs-lookup"><span data-stu-id="a80bd-104">Methods</span></span>  
  
|<span data-ttu-id="a80bd-105">方法</span><span class="sxs-lookup"><span data-stu-id="a80bd-105">Method</span></span>|<span data-ttu-id="a80bd-106">描述</span><span class="sxs-lookup"><span data-stu-id="a80bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a80bd-107">ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="a80bd-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="a80bd-108">通知主機傳送此回呼的執行緒即將在偵錯工具中封鎖。</span><span class="sxs-lookup"><span data-stu-id="a80bd-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="a80bd-109">ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a80bd-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="a80bd-110">通知主機偵錯工具即將釋放所有封鎖的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a80bd-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="a80bd-111">StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="a80bd-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="a80bd-112">通知主機偵錯工具即將開始封鎖所有線程。</span><span class="sxs-lookup"><span data-stu-id="a80bd-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a80bd-113">需求</span><span class="sxs-lookup"><span data-stu-id="a80bd-113">Requirements</span></span>  
 <span data-ttu-id="a80bd-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a80bd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80bd-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a80bd-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a80bd-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a80bd-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a80bd-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a80bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80bd-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="a80bd-118">See also</span></span>

- [<span data-ttu-id="a80bd-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a80bd-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
