---
title: ICLRControl::SetAppDomainManagerType 方法
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: 28fdd5340aee0fcd9875dd983c8c7649b5491c04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674706"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="1e458-102">ICLRControl::SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="1e458-102">ICLRControl::SetAppDomainManagerType Method</span></span>

<span data-ttu-id="1e458-103">將衍生自的型別設定 <xref:System.AppDomainManager> 為應用程式域管理員的型別。</span><span class="sxs-lookup"><span data-stu-id="1e458-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e458-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e458-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e458-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e458-105">Parameters</span></span>  

 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="1e458-106">在實作為衍生自之要求型別的元件名稱 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="1e458-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="1e458-107">在在參數中實作為的型別名稱 `pwzAppDomainManagerAssembly` ，這個參數會執行的功能 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="1e458-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e458-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e458-108">Return Value</span></span>  
  
|<span data-ttu-id="1e458-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e458-109">HRESULT</span></span>|<span data-ttu-id="1e458-110">描述</span><span class="sxs-lookup"><span data-stu-id="1e458-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e458-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e458-111">S_OK</span></span>|<span data-ttu-id="1e458-112">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1e458-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="1e458-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e458-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e458-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1e458-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e458-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e458-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e458-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="1e458-116">The call timed out.</span></span>|  
|<span data-ttu-id="1e458-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e458-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e458-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1e458-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e458-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e458-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e458-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="1e458-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e458-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e458-121">E_FAIL</span></span>|<span data-ttu-id="1e458-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1e458-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e458-123">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="1e458-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e458-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1e458-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e458-125">需求</span><span class="sxs-lookup"><span data-stu-id="1e458-125">Requirements</span></span>  

 <span data-ttu-id="1e458-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e458-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e458-127">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1e458-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e458-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1e458-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e458-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e458-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e458-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e458-130">See also</span></span>

- [<span data-ttu-id="1e458-131">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="1e458-131">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1e458-132">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="1e458-132">IHostControl Interface</span></span>](ihostcontrol-interface.md)
