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
ms.openlocfilehash: fa9608423456caeb6020e883a14f2c41583ac4d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126604"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="8ceb0-102">ICLRControl::GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="8ceb0-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="8ceb0-103">取得主機可以用來設定 common language runtime （CLR）之任何管理員類型的實例介面指標。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ceb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ceb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ceb0-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ceb0-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="8ceb0-106">在要傳回之管理員類型的 `IID`。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="8ceb0-107">支援下列 `IID` 值。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="8ceb0-108">IID_ICLRDebugManager：指定 `ppObject` 的類型會是[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8ceb0-109">IID_ICLRErrorReportingManager：指定 `ppObject` 的類型會是[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8ceb0-110">IID_ICLRGCManager：指定 `ppObject` 的類型會是[ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8ceb0-111">IID_ICLRHostProtectionManager：指定 `ppObject` 的類型會是[ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8ceb0-112">IID_ICLROnEventManager：指定 `ppObject` 的類型會是[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8ceb0-113">IID_ICLRPolicyManager：指定 `ppObject` 的類型會是[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="8ceb0-114">IID_ICLRTaskManager：指定 `ppObject` 的類型會是[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="8ceb0-115">脫銷要求之管理員的介面指標，如果要求的管理員類型無效，則為 null。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ceb0-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="8ceb0-116">Return Value</span></span>  
  
|<span data-ttu-id="8ceb0-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ceb0-117">HRESULT</span></span>|<span data-ttu-id="8ceb0-118">描述</span><span class="sxs-lookup"><span data-stu-id="8ceb0-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ceb0-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ceb0-119">S_OK</span></span>|<span data-ttu-id="8ceb0-120">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="8ceb0-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ceb0-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ceb0-122">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ceb0-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ceb0-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ceb0-124">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-124">The call timed out.</span></span>|  
|<span data-ttu-id="8ceb0-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ceb0-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ceb0-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ceb0-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ceb0-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ceb0-128">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ceb0-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ceb0-129">E_FAIL</span></span>|<span data-ttu-id="8ceb0-130">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ceb0-131">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ceb0-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ceb0-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8ceb0-133">E_NOINTERFACE</span></span>|<span data-ttu-id="8ceb0-134">不支援介面類別型。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ceb0-135">需求</span><span class="sxs-lookup"><span data-stu-id="8ceb0-135">Requirements</span></span>  
 <span data-ttu-id="8ceb0-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ceb0-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ceb0-137">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8ceb0-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ceb0-138">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8ceb0-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ceb0-139">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ceb0-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ceb0-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ceb0-140">See also</span></span>

- [<span data-ttu-id="8ceb0-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8ceb0-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8ceb0-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="8ceb0-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
