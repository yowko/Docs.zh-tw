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
ms.openlocfilehash: 33c790bf2721f09b263494e845356ef6b6712f99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177134"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="83306-102">ICLRControl::GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="83306-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="83306-103">取得任何主應用程式可用來設定 common language runtime (CLR) 的管理員型別的執行個體的介面指標。</span><span class="sxs-lookup"><span data-stu-id="83306-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83306-104">語法</span><span class="sxs-lookup"><span data-stu-id="83306-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83306-105">參數</span><span class="sxs-lookup"><span data-stu-id="83306-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="83306-106">[in]`IID`管理員類型，傳回。</span><span class="sxs-lookup"><span data-stu-id="83306-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="83306-107">下列`IID`支援值。</span><span class="sxs-lookup"><span data-stu-id="83306-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="83306-108">IID_ICLRDebugManager:指定`ppObject`的類型會是[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="83306-109">IID_ICLRErrorReportingManager:指定`ppObject`的類型會是[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="83306-110">IID_ICLRGCManager:指定`ppObject`的類型會是[ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="83306-111">IID_ICLRHostProtectionManager:指定`ppObject`的類型會是[ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="83306-112">IID_ICLROnEventManager:指定`ppObject`的類型會是[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="83306-113">IID_ICLRPolicyManager:指定`ppObject`的類型會是[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="83306-114">IID_ICLRTaskManager: speciries 所`ppObject`的類型會是[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="83306-115">[out]要求的管理員] 中或如果要求不正確的管理員類型的 null 介面指標。</span><span class="sxs-lookup"><span data-stu-id="83306-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83306-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="83306-116">Return Value</span></span>  
  
|<span data-ttu-id="83306-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83306-117">HRESULT</span></span>|<span data-ttu-id="83306-118">描述</span><span class="sxs-lookup"><span data-stu-id="83306-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83306-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="83306-119">S_OK</span></span>|<span data-ttu-id="83306-120">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="83306-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="83306-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83306-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83306-122">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="83306-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83306-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83306-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83306-124">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="83306-124">The call timed out.</span></span>|  
|<span data-ttu-id="83306-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83306-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83306-126">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="83306-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83306-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83306-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83306-128">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="83306-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83306-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83306-129">E_FAIL</span></span>|<span data-ttu-id="83306-130">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="83306-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83306-131">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="83306-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83306-132">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="83306-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="83306-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="83306-133">E_NOINTERFACE</span></span>|<span data-ttu-id="83306-134">不支援的介面型別。</span><span class="sxs-lookup"><span data-stu-id="83306-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83306-135">需求</span><span class="sxs-lookup"><span data-stu-id="83306-135">Requirements</span></span>  
 <span data-ttu-id="83306-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83306-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83306-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83306-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83306-138">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83306-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="83306-139">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="83306-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83306-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83306-140">See also</span></span>

- [<span data-ttu-id="83306-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="83306-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="83306-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="83306-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
