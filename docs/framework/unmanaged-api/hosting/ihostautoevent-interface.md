---
title: IHostAutoEvent 介面
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: 6893b019c7e86d3f359cf64752d30f7896203786
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680855"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="6eb9b-102">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6eb9b-102">IHostAutoEvent Interface</span></span>

<span data-ttu-id="6eb9b-103">提供主機自動重設事件的標記法。</span><span class="sxs-lookup"><span data-stu-id="6eb9b-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6eb9b-104">方法</span><span class="sxs-lookup"><span data-stu-id="6eb9b-104">Methods</span></span>  
  
|<span data-ttu-id="6eb9b-105">方法</span><span class="sxs-lookup"><span data-stu-id="6eb9b-105">Method</span></span>|<span data-ttu-id="6eb9b-106">描述</span><span class="sxs-lookup"><span data-stu-id="6eb9b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6eb9b-107">Set 方法</span><span class="sxs-lookup"><span data-stu-id="6eb9b-107">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="6eb9b-108">將目前的 `IHostAutoEvent` 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="6eb9b-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="6eb9b-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="6eb9b-109">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="6eb9b-110">導致目前的 `IHostAutoEvent` 實例等到事件擁有或經過指定的時間量為止。</span><span class="sxs-lookup"><span data-stu-id="6eb9b-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6eb9b-111">需求</span><span class="sxs-lookup"><span data-stu-id="6eb9b-111">Requirements</span></span>  

 <span data-ttu-id="6eb9b-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb9b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb9b-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6eb9b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6eb9b-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6eb9b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb9b-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb9b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb9b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb9b-116">See also</span></span>

- [<span data-ttu-id="6eb9b-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6eb9b-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6eb9b-118">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6eb9b-118">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="6eb9b-119">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6eb9b-119">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="6eb9b-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6eb9b-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
