---
title: IHostPolicyManager::OnFailure 方法
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 8ad4943aa9bf1b66b34bcd83a5422a977b16518d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804223"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="bebfb-102">IHostPolicyManager::OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="bebfb-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="bebfb-103">通知主機 common language runtime （CLR）即將採取[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)方法呼叫所指定的動作，以回應資源配置或回收失敗。</span><span class="sxs-lookup"><span data-stu-id="bebfb-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bebfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="bebfb-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bebfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="bebfb-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="bebfb-106">在其中一個[EClrFailure](eclrfailure-enumeration.md)值，表示 CLR 回應的失敗類型。</span><span class="sxs-lookup"><span data-stu-id="bebfb-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="bebfb-107">在其中一個[EPolicyAction](epolicyaction-enumeration.md)值，表示 CLR 為了回應而採取的動作 `failure` 。</span><span class="sxs-lookup"><span data-stu-id="bebfb-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bebfb-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="bebfb-108">Return Value</span></span>  
  
|<span data-ttu-id="bebfb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bebfb-109">HRESULT</span></span>|<span data-ttu-id="bebfb-110">描述</span><span class="sxs-lookup"><span data-stu-id="bebfb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bebfb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bebfb-111">S_OK</span></span>|<span data-ttu-id="bebfb-112">`OnFailure`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="bebfb-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="bebfb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bebfb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bebfb-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bebfb-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bebfb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bebfb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bebfb-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="bebfb-116">The call timed out.</span></span>|  
|<span data-ttu-id="bebfb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bebfb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bebfb-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bebfb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bebfb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bebfb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bebfb-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="bebfb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bebfb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bebfb-121">E_FAIL</span></span>|<span data-ttu-id="bebfb-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bebfb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bebfb-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="bebfb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bebfb-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bebfb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bebfb-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="bebfb-125">Requirements</span></span>  
 <span data-ttu-id="bebfb-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bebfb-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bebfb-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="bebfb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bebfb-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bebfb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bebfb-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bebfb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bebfb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bebfb-130">See also</span></span>

- [<span data-ttu-id="bebfb-131">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="bebfb-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="bebfb-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="bebfb-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="bebfb-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="bebfb-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="bebfb-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="bebfb-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
