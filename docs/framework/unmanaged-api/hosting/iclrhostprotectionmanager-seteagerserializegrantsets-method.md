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
ms.openlocfilehash: e9bddaa25ba83570389a9d70ac1a9f60357f533c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432218"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="a639f-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法</span><span class="sxs-lookup"><span data-stu-id="a639f-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="a639f-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="a639f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a639f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a639f-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a639f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a639f-105">Return Value</span></span>  
  
|<span data-ttu-id="a639f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a639f-106">HRESULT</span></span>|<span data-ttu-id="a639f-107">描述</span><span class="sxs-lookup"><span data-stu-id="a639f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a639f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a639f-108">S_OK</span></span>|<span data-ttu-id="a639f-109">`SetEagerSerializeGrantSets` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a639f-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="a639f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a639f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a639f-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a639f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a639f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a639f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a639f-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a639f-113">The call timed out.</span></span>|  
|<span data-ttu-id="a639f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a639f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a639f-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a639f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a639f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a639f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a639f-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a639f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a639f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a639f-118">E_FAIL</span></span>|<span data-ttu-id="a639f-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a639f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a639f-120">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a639f-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a639f-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a639f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a639f-122">需求</span><span class="sxs-lookup"><span data-stu-id="a639f-122">Requirements</span></span>  
 <span data-ttu-id="a639f-123">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a639f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a639f-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a639f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a639f-125">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a639f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a639f-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a639f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a639f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a639f-127">See Also</span></span>  
 [<span data-ttu-id="a639f-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="a639f-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a639f-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a639f-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
