---
title: "IDebuggerThreadControl 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IDebuggerThreadControl
helpviewer_keywords: IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e3f8d04a47607958ff5d439b501a6de9bbc5b02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="25721-102">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="25721-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="25721-103">提供方法來通知主機有關封鎖及解除封鎖的執行緒，偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="25721-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25721-104">方法</span><span class="sxs-lookup"><span data-stu-id="25721-104">Methods</span></span>  
  
|<span data-ttu-id="25721-105">方法</span><span class="sxs-lookup"><span data-stu-id="25721-105">Method</span></span>|<span data-ttu-id="25721-106">說明</span><span class="sxs-lookup"><span data-stu-id="25721-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25721-107">ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="25721-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="25721-108">通知會傳送此回呼執行緒相關的主機至偵錯服務內的區塊。</span><span class="sxs-lookup"><span data-stu-id="25721-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="25721-109">ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="25721-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="25721-110">通知主機有偵錯服務即將要釋放所有的執行緒所封鎖。</span><span class="sxs-lookup"><span data-stu-id="25721-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="25721-111">StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="25721-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="25721-112">通知主機偵錯服務即將開始封鎖所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="25721-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25721-113">需求</span><span class="sxs-lookup"><span data-stu-id="25721-113">Requirements</span></span>  
 <span data-ttu-id="25721-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25721-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25721-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25721-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25721-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25721-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25721-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25721-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25721-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25721-118">See Also</span></span>  
 [<span data-ttu-id="25721-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="25721-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
