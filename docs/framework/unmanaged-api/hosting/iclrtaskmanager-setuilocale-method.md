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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1380864a66d904c26ece14899de78b1b5b7f0408
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437140"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="f04bc-102">ICLRTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="f04bc-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="f04bc-103">通知目前執行之工作的 common language runtime (CLR) 主機已修改使用者介面 (UI) 地區設定或文化特性。</span><span class="sxs-lookup"><span data-stu-id="f04bc-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f04bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f04bc-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f04bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="f04bc-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f04bc-106">[in]對應到新指派的地理文化特性和使用者介面的語言地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="f04bc-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f04bc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f04bc-107">Return Value</span></span>  
  
|<span data-ttu-id="f04bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f04bc-108">HRESULT</span></span>|<span data-ttu-id="f04bc-109">描述</span><span class="sxs-lookup"><span data-stu-id="f04bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f04bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f04bc-110">S_OK</span></span>|<span data-ttu-id="f04bc-111">`SetUILocale` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f04bc-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="f04bc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f04bc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f04bc-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f04bc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f04bc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f04bc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f04bc-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f04bc-115">The call timed out.</span></span>|  
|<span data-ttu-id="f04bc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f04bc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f04bc-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f04bc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f04bc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f04bc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f04bc-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f04bc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f04bc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f04bc-120">E_FAIL</span></span>|<span data-ttu-id="f04bc-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f04bc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f04bc-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f04bc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f04bc-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f04bc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f04bc-124">備註</span><span class="sxs-lookup"><span data-stu-id="f04bc-124">Remarks</span></span>  
 <span data-ttu-id="f04bc-125">`SetUILocale` 提供執行可能會有任何機制進行地區設定的同步處理主機的機會。</span><span class="sxs-lookup"><span data-stu-id="f04bc-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f04bc-126">需求</span><span class="sxs-lookup"><span data-stu-id="f04bc-126">Requirements</span></span>  
 <span data-ttu-id="f04bc-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f04bc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f04bc-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f04bc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f04bc-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f04bc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f04bc-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f04bc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f04bc-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f04bc-131">See Also</span></span>  
 [<span data-ttu-id="f04bc-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f04bc-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f04bc-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f04bc-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f04bc-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f04bc-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f04bc-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f04bc-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
