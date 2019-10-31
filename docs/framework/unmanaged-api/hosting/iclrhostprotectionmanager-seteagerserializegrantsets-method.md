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
ms.openlocfilehash: be59acea8eadb0da9e3cd26cf17eb9e1617c3575
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141069"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="594da-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法</span><span class="sxs-lookup"><span data-stu-id="594da-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="594da-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="594da-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="594da-104">語法</span><span class="sxs-lookup"><span data-stu-id="594da-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="594da-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="594da-105">Return Value</span></span>  
  
|<span data-ttu-id="594da-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="594da-106">HRESULT</span></span>|<span data-ttu-id="594da-107">描述</span><span class="sxs-lookup"><span data-stu-id="594da-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="594da-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="594da-108">S_OK</span></span>|<span data-ttu-id="594da-109">已成功傳回 `SetEagerSerializeGrantSets`。</span><span class="sxs-lookup"><span data-stu-id="594da-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="594da-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="594da-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="594da-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="594da-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="594da-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="594da-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="594da-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="594da-113">The call timed out.</span></span>|  
|<span data-ttu-id="594da-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="594da-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="594da-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="594da-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="594da-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="594da-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="594da-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="594da-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="594da-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="594da-118">E_FAIL</span></span>|<span data-ttu-id="594da-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="594da-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="594da-120">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="594da-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="594da-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="594da-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="594da-122">需求</span><span class="sxs-lookup"><span data-stu-id="594da-122">Requirements</span></span>  
 <span data-ttu-id="594da-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="594da-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="594da-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="594da-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="594da-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="594da-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="594da-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="594da-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594da-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="594da-127">See also</span></span>

- [<span data-ttu-id="594da-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="594da-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="594da-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="594da-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
