---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948fd78ae2839bd24a44c8c0b806e32b1da7125f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729769"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="05d8b-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法</span><span class="sxs-lookup"><span data-stu-id="05d8b-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="05d8b-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="05d8b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="05d8b-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05d8b-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="05d8b-105">Return Value</span></span>  
  
|<span data-ttu-id="05d8b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05d8b-106">HRESULT</span></span>|<span data-ttu-id="05d8b-107">描述</span><span class="sxs-lookup"><span data-stu-id="05d8b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05d8b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="05d8b-108">S_OK</span></span>|<span data-ttu-id="05d8b-109">`SetEagerSerializeGrantSets` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="05d8b-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="05d8b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05d8b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05d8b-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="05d8b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05d8b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05d8b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05d8b-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="05d8b-113">The call timed out.</span></span>|  
|<span data-ttu-id="05d8b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05d8b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05d8b-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="05d8b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05d8b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05d8b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05d8b-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="05d8b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05d8b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05d8b-118">E_FAIL</span></span>|<span data-ttu-id="05d8b-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="05d8b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05d8b-120">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="05d8b-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05d8b-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="05d8b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05d8b-122">需求</span><span class="sxs-lookup"><span data-stu-id="05d8b-122">Requirements</span></span>  
 <span data-ttu-id="05d8b-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05d8b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d8b-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05d8b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05d8b-125">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="05d8b-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05d8b-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d8b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d8b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d8b-127">See also</span></span>
- [<span data-ttu-id="05d8b-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="05d8b-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="05d8b-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="05d8b-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
