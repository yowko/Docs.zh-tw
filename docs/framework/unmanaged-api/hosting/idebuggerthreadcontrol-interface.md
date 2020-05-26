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
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805282"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="ee975-102">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="ee975-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="ee975-103">提供方法，以通知主機有關偵錯工具的執行緒封鎖和解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="ee975-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee975-104">方法</span><span class="sxs-lookup"><span data-stu-id="ee975-104">Methods</span></span>  
  
|<span data-ttu-id="ee975-105">方法</span><span class="sxs-lookup"><span data-stu-id="ee975-105">Method</span></span>|<span data-ttu-id="ee975-106">描述</span><span class="sxs-lookup"><span data-stu-id="ee975-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee975-107">ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="ee975-107">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="ee975-108">通知主機傳送此回呼的執行緒即將在偵錯工具中封鎖。</span><span class="sxs-lookup"><span data-stu-id="ee975-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="ee975-109">ReleaseAllRuntimeThreads 方法</span><span class="sxs-lookup"><span data-stu-id="ee975-109">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="ee975-110">通知主機偵錯工具即將釋放所有封鎖的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ee975-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="ee975-111">StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="ee975-111">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="ee975-112">通知主機偵錯工具即將開始封鎖所有線程。</span><span class="sxs-lookup"><span data-stu-id="ee975-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee975-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="ee975-113">Requirements</span></span>  
 <span data-ttu-id="ee975-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee975-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee975-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ee975-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee975-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ee975-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee975-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee975-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee975-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee975-118">See also</span></span>

- [<span data-ttu-id="ee975-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ee975-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
