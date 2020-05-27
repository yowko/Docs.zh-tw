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
ms.openlocfilehash: 55fd858927743b097e5e842c0897a16d36b76733
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804977"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="7bac9-102">IHostAutoEvent::Set 方法</span><span class="sxs-lookup"><span data-stu-id="7bac9-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="7bac9-103">將目前的[IHostAutoEvent](ihostautoevent-interface.md)實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="7bac9-103">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bac9-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bac9-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7bac9-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bac9-105">Return Value</span></span>  
  
|<span data-ttu-id="7bac9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bac9-106">HRESULT</span></span>|<span data-ttu-id="7bac9-107">描述</span><span class="sxs-lookup"><span data-stu-id="7bac9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bac9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bac9-108">S_OK</span></span>|<span data-ttu-id="7bac9-109">`Set`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7bac9-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="7bac9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bac9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bac9-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7bac9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bac9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bac9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bac9-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="7bac9-113">The call timed out.</span></span>|  
|<span data-ttu-id="7bac9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bac9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bac9-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7bac9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bac9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bac9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bac9-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="7bac9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bac9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bac9-118">E_FAIL</span></span>|<span data-ttu-id="7bac9-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7bac9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bac9-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="7bac9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bac9-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7bac9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bac9-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="7bac9-122">Requirements</span></span>  
 <span data-ttu-id="7bac9-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bac9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bac9-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7bac9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bac9-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7bac9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bac9-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bac9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bac9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bac9-127">See also</span></span>

- [<span data-ttu-id="7bac9-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7bac9-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7bac9-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="7bac9-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="7bac9-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="7bac9-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="7bac9-131">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7bac9-131">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
