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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a551d3cc6ab3dd3887f232018f8201de4036d1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096832"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="0ad4d-102">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="0ad4d-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="0ad4d-103">提供方法來通知主機有關封鎖和解除封鎖執行緒的偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="0ad4d-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ad4d-104">方法</span><span class="sxs-lookup"><span data-stu-id="0ad4d-104">Methods</span></span>  
  
|<span data-ttu-id="0ad4d-105">方法</span><span class="sxs-lookup"><span data-stu-id="0ad4d-105">Method</span></span>|<span data-ttu-id="0ad4d-106">描述</span><span class="sxs-lookup"><span data-stu-id="0ad4d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ad4d-107">ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="0ad4d-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="0ad4d-108">通知主機有關的傳送此回呼的執行緒偵錯服務內的區塊。</span><span class="sxs-lookup"><span data-stu-id="0ad4d-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="0ad4d-109">ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0ad4d-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="0ad4d-110">主應用程式的偵錯的服務是即將要釋放所有封鎖的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0ad4d-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="0ad4d-111">StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="0ad4d-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="0ad4d-112">主應用程式的偵錯服務即將開始封鎖所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="0ad4d-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ad4d-113">需求</span><span class="sxs-lookup"><span data-stu-id="0ad4d-113">Requirements</span></span>  
 <span data-ttu-id="0ad4d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad4d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ad4d-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ad4d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ad4d-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ad4d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ad4d-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ad4d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad4d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad4d-118">See also</span></span>

- [<span data-ttu-id="0ad4d-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="0ad4d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
