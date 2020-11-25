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
ms.openlocfilehash: 9ce4a5e042e838da8e9eba614f26e35b38af56c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714129"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="a4bc6-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets 方法</span><span class="sxs-lookup"><span data-stu-id="a4bc6-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>

<span data-ttu-id="a4bc6-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4bc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4bc6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a4bc6-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4bc6-105">Return Value</span></span>  
  
|<span data-ttu-id="a4bc6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4bc6-106">HRESULT</span></span>|<span data-ttu-id="a4bc6-107">描述</span><span class="sxs-lookup"><span data-stu-id="a4bc6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4bc6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4bc6-108">S_OK</span></span>|<span data-ttu-id="a4bc6-109">`SetEagerSerializeGrantSets` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="a4bc6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4bc6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4bc6-111">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4bc6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4bc6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4bc6-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-113">The call timed out.</span></span>|  
|<span data-ttu-id="a4bc6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4bc6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4bc6-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4bc6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4bc6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4bc6-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4bc6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4bc6-118">E_FAIL</span></span>|<span data-ttu-id="a4bc6-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4bc6-120">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4bc6-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4bc6-122">需求</span><span class="sxs-lookup"><span data-stu-id="a4bc6-122">Requirements</span></span>  

 <span data-ttu-id="a4bc6-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4bc6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4bc6-124">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a4bc6-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4bc6-125">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a4bc6-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4bc6-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4bc6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4bc6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4bc6-127">See also</span></span>

- [<span data-ttu-id="a4bc6-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="a4bc6-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a4bc6-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a4bc6-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
