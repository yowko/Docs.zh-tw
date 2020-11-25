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
ms.openlocfilehash: d18b3a5c06ac0d3a86f7823f3b140c76c6c9a746
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728351"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="1b106-102">ICLRControl::GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="1b106-102">ICLRControl::GetCLRManager Method</span></span>

<span data-ttu-id="1b106-103">取得任何管理員型別的實例介面指標，主機可以用來設定 common language runtime (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="1b106-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b106-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b106-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b106-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b106-105">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="1b106-106">在要傳回的 `IID` 管理員型別的。</span><span class="sxs-lookup"><span data-stu-id="1b106-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="1b106-107">支援下列 `IID` 值。</span><span class="sxs-lookup"><span data-stu-id="1b106-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="1b106-108">IID_ICLRDebugManager：指定 `ppObject` 將為 [ICLRDebugManager](iclrdebugmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="1b106-109">IID_ICLRErrorReportingManager：指定 `ppObject` 將為 [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="1b106-110">IID_ICLRGCManager：指定 `ppObject` 將為 [ICLRGCManager](iclrgcmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="1b106-111">IID_ICLRHostProtectionManager：指定 `ppObject` 將為 [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="1b106-112">IID_ICLROnEventManager：指定 `ppObject` 將為 [ICLROnEventManager](iclroneventmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="1b106-113">IID_ICLRPolicyManager：指定 `ppObject` 將為 [ICLRPolicyManager](iclrpolicymanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="1b106-114">IID_ICLRTaskManager：指定 `ppObject` 將為 [ICLRTaskManager](iclrtaskmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="1b106-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="1b106-115">擴展要求的管理員的介面指標，如果要求的管理員類型無效，則為 null。</span><span class="sxs-lookup"><span data-stu-id="1b106-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b106-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b106-116">Return Value</span></span>  
  
|<span data-ttu-id="1b106-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b106-117">HRESULT</span></span>|<span data-ttu-id="1b106-118">描述</span><span class="sxs-lookup"><span data-stu-id="1b106-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b106-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b106-119">S_OK</span></span>|<span data-ttu-id="1b106-120">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1b106-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="1b106-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b106-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b106-122">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1b106-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b106-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b106-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b106-124">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="1b106-124">The call timed out.</span></span>|  
|<span data-ttu-id="1b106-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b106-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b106-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1b106-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b106-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b106-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b106-128">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="1b106-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b106-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b106-129">E_FAIL</span></span>|<span data-ttu-id="1b106-130">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1b106-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b106-131">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="1b106-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b106-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1b106-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b106-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="1b106-133">E_NOINTERFACE</span></span>|<span data-ttu-id="1b106-134">不支援介面類別型。</span><span class="sxs-lookup"><span data-stu-id="1b106-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b106-135">需求</span><span class="sxs-lookup"><span data-stu-id="1b106-135">Requirements</span></span>  

 <span data-ttu-id="1b106-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b106-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b106-137">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1b106-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b106-138">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1b106-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b106-139">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b106-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b106-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b106-140">See also</span></span>

- [<span data-ttu-id="1b106-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="1b106-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1b106-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="1b106-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
