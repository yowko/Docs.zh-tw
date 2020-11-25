---
title: ICLRTaskManager::SetUILocale 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: a426fca1b7ca4bfb9cbb30a221859f7c114db682
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732420"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="4a225-102">ICLRTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="4a225-102">ICLRTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="4a225-103">通知 common language runtime (CLR) 主機已針對目前執行中的工作修改使用者介面 (UI) 地區設定或文化特性。</span><span class="sxs-lookup"><span data-stu-id="4a225-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a225-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a225-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a225-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a225-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="4a225-106">在地區設定識別碼值，對應至新指派的使用者介面地理文化特性和語言。</span><span class="sxs-lookup"><span data-stu-id="4a225-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a225-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4a225-107">Return Value</span></span>  
  
|<span data-ttu-id="4a225-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a225-108">HRESULT</span></span>|<span data-ttu-id="4a225-109">描述</span><span class="sxs-lookup"><span data-stu-id="4a225-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a225-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a225-110">S_OK</span></span>|<span data-ttu-id="4a225-111">`SetUILocale` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="4a225-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="4a225-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a225-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a225-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4a225-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a225-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a225-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a225-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="4a225-115">The call timed out.</span></span>|  
|<span data-ttu-id="4a225-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a225-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a225-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4a225-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a225-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a225-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a225-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="4a225-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a225-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a225-120">E_FAIL</span></span>|<span data-ttu-id="4a225-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4a225-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a225-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="4a225-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a225-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4a225-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a225-124">備註</span><span class="sxs-lookup"><span data-stu-id="4a225-124">Remarks</span></span>  

 <span data-ttu-id="4a225-125">`SetUILocale` 提供機會讓主機執行任何可能會對地區設定進行同步處理的機制。</span><span class="sxs-lookup"><span data-stu-id="4a225-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a225-126">需求</span><span class="sxs-lookup"><span data-stu-id="4a225-126">Requirements</span></span>  

 <span data-ttu-id="4a225-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a225-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a225-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4a225-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a225-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4a225-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a225-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a225-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a225-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a225-131">See also</span></span>

- [<span data-ttu-id="4a225-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4a225-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4a225-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4a225-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4a225-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4a225-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4a225-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4a225-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
