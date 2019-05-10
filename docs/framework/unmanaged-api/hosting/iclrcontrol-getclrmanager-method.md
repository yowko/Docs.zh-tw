---
title: ICLRControl::GetCLRManager 方法
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97d75eb5fab396530a6f48314e96c8d47d06439
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656491"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="a012a-102">ICLRControl::GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="a012a-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="a012a-103">取得任何主應用程式可用來設定 common language runtime (CLR) 的管理員型別的執行個體的介面指標。</span><span class="sxs-lookup"><span data-stu-id="a012a-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a012a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a012a-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a012a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a012a-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="a012a-106">[in]`IID`管理員類型，傳回。</span><span class="sxs-lookup"><span data-stu-id="a012a-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="a012a-107">下列`IID`支援值。</span><span class="sxs-lookup"><span data-stu-id="a012a-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="a012a-108">IID_ICLRDebugManager:指定`ppObject`的類型會是[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="a012a-109">IID_ICLRErrorReportingManager:指定`ppObject`的類型會是[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="a012a-110">IID_ICLRGCManager:指定`ppObject`的類型會是[ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="a012a-111">IID_ICLRHostProtectionManager:指定`ppObject`的類型會是[ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="a012a-112">IID_ICLROnEventManager:指定`ppObject`的類型會是[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="a012a-113">IID_ICLRPolicyManager:指定`ppObject`的類型會是[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="a012a-114">IID_ICLRTaskManager:指定`ppObject`的類型會是[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="a012a-115">[out]要求的管理員 中或如果要求不正確的管理員類型的 null 介面指標。</span><span class="sxs-lookup"><span data-stu-id="a012a-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a012a-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="a012a-116">Return Value</span></span>  
  
|<span data-ttu-id="a012a-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a012a-117">HRESULT</span></span>|<span data-ttu-id="a012a-118">描述</span><span class="sxs-lookup"><span data-stu-id="a012a-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a012a-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="a012a-119">S_OK</span></span>|<span data-ttu-id="a012a-120">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a012a-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="a012a-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a012a-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a012a-122">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a012a-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a012a-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a012a-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a012a-124">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a012a-124">The call timed out.</span></span>|  
|<span data-ttu-id="a012a-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a012a-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a012a-126">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a012a-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a012a-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a012a-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a012a-128">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a012a-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a012a-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a012a-129">E_FAIL</span></span>|<span data-ttu-id="a012a-130">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a012a-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a012a-131">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a012a-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a012a-132">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a012a-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a012a-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="a012a-133">E_NOINTERFACE</span></span>|<span data-ttu-id="a012a-134">不支援的介面型別。</span><span class="sxs-lookup"><span data-stu-id="a012a-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a012a-135">需求</span><span class="sxs-lookup"><span data-stu-id="a012a-135">Requirements</span></span>  
 <span data-ttu-id="a012a-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a012a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a012a-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a012a-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a012a-138">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a012a-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a012a-139">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a012a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a012a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a012a-140">See also</span></span>

- [<span data-ttu-id="a012a-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="a012a-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a012a-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="a012a-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
