---
title: IHostPolicyManager::OnDefaultAction 方法
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: a22f16c14514b90ce888fafc0ea554bd9f90cb11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684079"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="91898-102">IHostPolicyManager::OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="91898-102">IHostPolicyManager::OnDefaultAction Method</span></span>

<span data-ttu-id="91898-103">通知主機 common language runtime (CLR) 即將採用呼叫 [ICLRPolicyManager：： SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) 方法所設定的預設動作，以回應執行緒中止或卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="91898-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91898-104">語法</span><span class="sxs-lookup"><span data-stu-id="91898-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91898-105">參數</span><span class="sxs-lookup"><span data-stu-id="91898-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="91898-106">在其中一個 [EClrOperation](eclroperation-enumeration.md) 值，表示 CLR 回應的事件種類。</span><span class="sxs-lookup"><span data-stu-id="91898-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="91898-107">在其中一個 [EPolicyAction](epolicyaction-enumeration.md) 值，表示 CLR 為了回應事件而採取的動作。</span><span class="sxs-lookup"><span data-stu-id="91898-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91898-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="91898-108">Return Value</span></span>  
  
|<span data-ttu-id="91898-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91898-109">HRESULT</span></span>|<span data-ttu-id="91898-110">描述</span><span class="sxs-lookup"><span data-stu-id="91898-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91898-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="91898-111">S_OK</span></span>|<span data-ttu-id="91898-112">`OnDefaultAction` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="91898-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="91898-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91898-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91898-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="91898-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="91898-115">成功</span><span class="sxs-lookup"><span data-stu-id="91898-115">successfully</span></span>|  
|<span data-ttu-id="91898-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91898-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91898-117">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="91898-117">The call timed out.</span></span>|  
|<span data-ttu-id="91898-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91898-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91898-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="91898-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91898-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91898-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91898-121">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="91898-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91898-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91898-122">E_FAIL</span></span>|<span data-ttu-id="91898-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="91898-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91898-124">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="91898-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91898-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="91898-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91898-126">需求</span><span class="sxs-lookup"><span data-stu-id="91898-126">Requirements</span></span>  

 <span data-ttu-id="91898-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91898-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91898-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="91898-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91898-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="91898-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91898-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91898-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91898-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91898-131">See also</span></span>

- [<span data-ttu-id="91898-132">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="91898-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="91898-133">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="91898-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="91898-134">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="91898-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="91898-135">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="91898-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
