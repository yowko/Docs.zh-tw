---
title: ICLROnEventManager::UnregisterActionOnEvent 方法
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54abd54662d4e99881dddf15876b596a4a705f70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638875"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="6d1e7-102">ICLROnEventManager::UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="6d1e7-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="6d1e7-103">取消註冊先前註冊的回呼指標為指定的事件。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d1e7-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d1e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d1e7-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="6d1e7-106">[in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，表示要取消註冊回呼指標所描述的事件`pAction`。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="6d1e7-107">[in]指標[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)做為參數傳遞的物件[RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d1e7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6d1e7-108">Return Value</span></span>  
  
|<span data-ttu-id="6d1e7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d1e7-109">HRESULT</span></span>|<span data-ttu-id="6d1e7-110">描述</span><span class="sxs-lookup"><span data-stu-id="6d1e7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d1e7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d1e7-111">S_OK</span></span>|<span data-ttu-id="6d1e7-112">`UnregisterActionOnEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="6d1e7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d1e7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d1e7-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d1e7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d1e7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d1e7-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-116">The call timed out.</span></span>|  
|<span data-ttu-id="6d1e7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d1e7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d1e7-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d1e7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d1e7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d1e7-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d1e7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d1e7-121">E_FAIL</span></span>|<span data-ttu-id="6d1e7-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d1e7-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d1e7-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d1e7-125">需求</span><span class="sxs-lookup"><span data-stu-id="6d1e7-125">Requirements</span></span>  
 <span data-ttu-id="6d1e7-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d1e7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1e7-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d1e7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d1e7-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6d1e7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d1e7-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1e7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1e7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d1e7-130">See also</span></span>

- [<span data-ttu-id="6d1e7-131">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="6d1e7-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="6d1e7-132">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="6d1e7-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="6d1e7-133">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="6d1e7-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6d1e7-134">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="6d1e7-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
