---
title: "ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1d2bb2ecc4ae7edb4edbaa3ff36650c70c82daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="190bc-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法</span><span class="sxs-lookup"><span data-stu-id="190bc-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="190bc-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="190bc-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="190bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="190bc-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="190bc-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="190bc-105">Return Value</span></span>  
  
|<span data-ttu-id="190bc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="190bc-106">HRESULT</span></span>|<span data-ttu-id="190bc-107">描述</span><span class="sxs-lookup"><span data-stu-id="190bc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="190bc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="190bc-108">S_OK</span></span>|<span data-ttu-id="190bc-109">`SetEagerSerializeGrantSets`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="190bc-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="190bc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="190bc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="190bc-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="190bc-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="190bc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="190bc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="190bc-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="190bc-113">The call timed out.</span></span>|  
|<span data-ttu-id="190bc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="190bc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="190bc-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="190bc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="190bc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="190bc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="190bc-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="190bc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="190bc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="190bc-118">E_FAIL</span></span>|<span data-ttu-id="190bc-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="190bc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="190bc-120">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="190bc-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="190bc-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="190bc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="190bc-122">需求</span><span class="sxs-lookup"><span data-stu-id="190bc-122">Requirements</span></span>  
 <span data-ttu-id="190bc-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="190bc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="190bc-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="190bc-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="190bc-125">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="190bc-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="190bc-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="190bc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190bc-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="190bc-127">See Also</span></span>  
 [<span data-ttu-id="190bc-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="190bc-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="190bc-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="190bc-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
