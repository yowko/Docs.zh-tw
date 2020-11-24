---
title: IHostPolicyManager::OnTimeout 方法
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: e3f2dc7ff9beaf417184f3d09db76e611982118a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690664"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="0042d-102">IHostPolicyManager::OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="0042d-102">IHostPolicyManager::OnTimeout Method</span></span>

<span data-ttu-id="0042d-103">通知主機 common language runtime (CLR) 即將採取 [ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) 方法呼叫所指定的動作，以回應超時。</span><span class="sxs-lookup"><span data-stu-id="0042d-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0042d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0042d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0042d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0042d-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="0042d-106">在其中一個 [EClrOperation](eclroperation-enumeration.md) 值，表示超時的作業種類。</span><span class="sxs-lookup"><span data-stu-id="0042d-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="0042d-107">在其中一個 [EPolicyAction](epolicyaction-enumeration.md) 值，表示 CLR 為了回應超時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0042d-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0042d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0042d-108">Return Value</span></span>  
  
|<span data-ttu-id="0042d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0042d-109">HRESULT</span></span>|<span data-ttu-id="0042d-110">描述</span><span class="sxs-lookup"><span data-stu-id="0042d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0042d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0042d-111">S_OK</span></span>|<span data-ttu-id="0042d-112">`OnTimeout` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="0042d-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="0042d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0042d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0042d-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0042d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0042d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0042d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0042d-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="0042d-116">The call timed out.</span></span>|  
|<span data-ttu-id="0042d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0042d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0042d-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0042d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0042d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0042d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0042d-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="0042d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0042d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0042d-121">E_FAIL</span></span>|<span data-ttu-id="0042d-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0042d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0042d-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="0042d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0042d-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0042d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0042d-125">需求</span><span class="sxs-lookup"><span data-stu-id="0042d-125">Requirements</span></span>  

 <span data-ttu-id="0042d-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0042d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0042d-127">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0042d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0042d-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0042d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0042d-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0042d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0042d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0042d-130">See also</span></span>

- [<span data-ttu-id="0042d-131">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="0042d-131">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="0042d-132">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="0042d-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="0042d-133">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0042d-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="0042d-134">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0042d-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
