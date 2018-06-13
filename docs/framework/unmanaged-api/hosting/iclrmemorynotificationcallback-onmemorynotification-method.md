---
title: ICLRMemoryNotificationCallback::OnMemoryNotification 方法
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 187c0a8d929958b7eaf1e99771da6a0d29c3d5f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434183"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="629c9-102">ICLRMemoryNotificationCallback::OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="629c9-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="629c9-103">通知 common language runtime (CLR) 的電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="629c9-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="629c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="629c9-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="629c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="629c9-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="629c9-106">[in]其中一個[EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)值，表示記憶體不足的壓力電腦目前發生。</span><span class="sxs-lookup"><span data-stu-id="629c9-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="629c9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="629c9-107">Return Value</span></span>  
  
|<span data-ttu-id="629c9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="629c9-108">HRESULT</span></span>|<span data-ttu-id="629c9-109">描述</span><span class="sxs-lookup"><span data-stu-id="629c9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="629c9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="629c9-110">S_OK</span></span>|<span data-ttu-id="629c9-111">`OnMemoryNotification` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="629c9-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="629c9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="629c9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="629c9-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="629c9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="629c9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="629c9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="629c9-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="629c9-115">The call timed out.</span></span>|  
|<span data-ttu-id="629c9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="629c9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="629c9-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="629c9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="629c9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="629c9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="629c9-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="629c9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="629c9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="629c9-120">E_FAIL</span></span>|<span data-ttu-id="629c9-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="629c9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="629c9-122">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="629c9-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="629c9-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="629c9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="629c9-124">備註</span><span class="sxs-lookup"><span data-stu-id="629c9-124">Remarks</span></span>  
 <span data-ttu-id="629c9-125">CLR 會註冊回呼`OnMemoryNotification`藉由呼叫[ihostmemorymanager:: Registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="629c9-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="629c9-126">執行階段主應用程式會報告的記憶體資源不足時，釋放額外的記憶體用於回呼中傳回的資訊。</span><span class="sxs-lookup"><span data-stu-id="629c9-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="629c9-127">呼叫`OnMemoryNotification`永遠不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="629c9-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="629c9-128">它們一律立即傳回。</span><span class="sxs-lookup"><span data-stu-id="629c9-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="629c9-129">需求</span><span class="sxs-lookup"><span data-stu-id="629c9-129">Requirements</span></span>  
 <span data-ttu-id="629c9-130">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="629c9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="629c9-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="629c9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="629c9-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="629c9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="629c9-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="629c9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629c9-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="629c9-134">See Also</span></span>  
 [<span data-ttu-id="629c9-135">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="629c9-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="629c9-136">RegisterMemoryNotificationCallback 方法</span><span class="sxs-lookup"><span data-stu-id="629c9-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="629c9-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="629c9-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
