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
ms.openlocfilehash: e911a8e73020321511da5bd7f3ade677058048e4
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703831"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="b964f-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法</span><span class="sxs-lookup"><span data-stu-id="b964f-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="b964f-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="b964f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b964f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b964f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b964f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="b964f-105">Return Value</span></span>  
  
|<span data-ttu-id="b964f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b964f-106">HRESULT</span></span>|<span data-ttu-id="b964f-107">說明</span><span class="sxs-lookup"><span data-stu-id="b964f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b964f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b964f-108">S_OK</span></span>|<span data-ttu-id="b964f-109">`SetEagerSerializeGrantSets`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b964f-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="b964f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b964f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b964f-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b964f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b964f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b964f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b964f-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b964f-113">The call timed out.</span></span>|  
|<span data-ttu-id="b964f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b964f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b964f-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b964f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b964f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b964f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b964f-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b964f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b964f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b964f-118">E_FAIL</span></span>|<span data-ttu-id="b964f-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b964f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b964f-120">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b964f-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b964f-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b964f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b964f-122">需求</span><span class="sxs-lookup"><span data-stu-id="b964f-122">Requirements</span></span>  
 <span data-ttu-id="b964f-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b964f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b964f-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b964f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b964f-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b964f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b964f-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b964f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b964f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b964f-127">See also</span></span>

- [<span data-ttu-id="b964f-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b964f-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b964f-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b964f-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
