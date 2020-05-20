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
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615848"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="42a6f-102">ICLRControl::GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="42a6f-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="42a6f-103">取得主機可以用來設定 common language runtime （CLR）之任何管理員類型的實例介面指標。</span><span class="sxs-lookup"><span data-stu-id="42a6f-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42a6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="42a6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42a6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="42a6f-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="42a6f-106">在`IID`要傳回之管理員類型的。</span><span class="sxs-lookup"><span data-stu-id="42a6f-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="42a6f-107">支援下列 `IID` 值。</span><span class="sxs-lookup"><span data-stu-id="42a6f-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="42a6f-108">IID_ICLRDebugManager：指定 `ppObject` 將屬於[ICLRDebugManager](iclrdebugmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="42a6f-109">IID_ICLRErrorReportingManager：指定 `ppObject` 將屬於[ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="42a6f-110">IID_ICLRGCManager：指定 `ppObject` 將屬於[ICLRGCManager](iclrgcmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="42a6f-111">IID_ICLRHostProtectionManager：指定 `ppObject` 將屬於[ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="42a6f-112">IID_ICLROnEventManager：指定 `ppObject` 將屬於[ICLROnEventManager](iclroneventmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="42a6f-113">IID_ICLRPolicyManager：指定 `ppObject` 將屬於[ICLRPolicyManager](iclrpolicymanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="42a6f-114">IID_ICLRTaskManager：指定 `ppObject` 將屬於[ICLRTaskManager](iclrtaskmanager-interface.md)類型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="42a6f-115">脫銷要求之管理員的介面指標，如果要求的管理員類型無效，則為 null。</span><span class="sxs-lookup"><span data-stu-id="42a6f-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42a6f-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="42a6f-116">Return Value</span></span>  
  
|<span data-ttu-id="42a6f-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42a6f-117">HRESULT</span></span>|<span data-ttu-id="42a6f-118">說明</span><span class="sxs-lookup"><span data-stu-id="42a6f-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42a6f-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="42a6f-119">S_OK</span></span>|<span data-ttu-id="42a6f-120">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="42a6f-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="42a6f-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42a6f-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42a6f-122">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="42a6f-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42a6f-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42a6f-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42a6f-124">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="42a6f-124">The call timed out.</span></span>|  
|<span data-ttu-id="42a6f-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42a6f-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42a6f-126">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="42a6f-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42a6f-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42a6f-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42a6f-128">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="42a6f-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42a6f-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42a6f-129">E_FAIL</span></span>|<span data-ttu-id="42a6f-130">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="42a6f-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42a6f-131">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="42a6f-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42a6f-132">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="42a6f-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42a6f-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="42a6f-133">E_NOINTERFACE</span></span>|<span data-ttu-id="42a6f-134">不支援介面類別型。</span><span class="sxs-lookup"><span data-stu-id="42a6f-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42a6f-135">需求</span><span class="sxs-lookup"><span data-stu-id="42a6f-135">Requirements</span></span>  
 <span data-ttu-id="42a6f-136">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42a6f-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42a6f-137">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="42a6f-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42a6f-138">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="42a6f-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42a6f-139">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42a6f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a6f-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42a6f-140">See also</span></span>

- [<span data-ttu-id="42a6f-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="42a6f-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="42a6f-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="42a6f-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
