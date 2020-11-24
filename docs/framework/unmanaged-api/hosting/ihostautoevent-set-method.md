---
title: IHostAutoEvent::Set 方法
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: facfbb85645f444b010cb1fe1c34bbe94011ac50
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680821"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="c69d2-102">IHostAutoEvent::Set 方法</span><span class="sxs-lookup"><span data-stu-id="c69d2-102">IHostAutoEvent::Set Method</span></span>

<span data-ttu-id="c69d2-103">將目前的 [IHostAutoEvent](ihostautoevent-interface.md) 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="c69d2-103">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c69d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="c69d2-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c69d2-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="c69d2-105">Return Value</span></span>  
  
|<span data-ttu-id="c69d2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c69d2-106">HRESULT</span></span>|<span data-ttu-id="c69d2-107">描述</span><span class="sxs-lookup"><span data-stu-id="c69d2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c69d2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c69d2-108">S_OK</span></span>|<span data-ttu-id="c69d2-109">`Set` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="c69d2-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="c69d2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c69d2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c69d2-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c69d2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c69d2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c69d2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c69d2-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="c69d2-113">The call timed out.</span></span>|  
|<span data-ttu-id="c69d2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c69d2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c69d2-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c69d2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c69d2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c69d2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c69d2-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="c69d2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c69d2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c69d2-118">E_FAIL</span></span>|<span data-ttu-id="c69d2-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c69d2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c69d2-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="c69d2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c69d2-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c69d2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c69d2-122">需求</span><span class="sxs-lookup"><span data-stu-id="c69d2-122">Requirements</span></span>  

 <span data-ttu-id="c69d2-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c69d2-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c69d2-124">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c69d2-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c69d2-125">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c69d2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c69d2-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c69d2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69d2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c69d2-127">See also</span></span>

- [<span data-ttu-id="c69d2-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c69d2-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c69d2-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="c69d2-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="c69d2-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="c69d2-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="c69d2-131">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c69d2-131">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
