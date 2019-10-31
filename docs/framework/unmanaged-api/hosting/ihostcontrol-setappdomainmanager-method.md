---
title: IHostControl::SetAppDomainManager 方法
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: de264135450190fd028eb8cf12017d94cc65ffac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134728"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="100c0-102">IHostControl::SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="100c0-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="100c0-103">通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="100c0-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="100c0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="100c0-105">參數</span><span class="sxs-lookup"><span data-stu-id="100c0-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="100c0-106">在所選取 <xref:System.AppDomain>的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="100c0-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="100c0-107">在主機實作為 `IUnknown`之 <xref:System.AppDomainManager> 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="100c0-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="100c0-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="100c0-108">Return Value</span></span>  
  
|<span data-ttu-id="100c0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="100c0-109">HRESULT</span></span>|<span data-ttu-id="100c0-110">描述</span><span class="sxs-lookup"><span data-stu-id="100c0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="100c0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="100c0-111">S_OK</span></span>|<span data-ttu-id="100c0-112">已成功傳回 `SetAppDomainManager`。</span><span class="sxs-lookup"><span data-stu-id="100c0-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="100c0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="100c0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="100c0-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="100c0-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="100c0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="100c0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="100c0-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="100c0-116">The call timed out.</span></span>|  
|<span data-ttu-id="100c0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="100c0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="100c0-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="100c0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="100c0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="100c0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="100c0-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="100c0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="100c0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="100c0-121">E_FAIL</span></span>|<span data-ttu-id="100c0-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="100c0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="100c0-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="100c0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="100c0-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="100c0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="100c0-125">備註</span><span class="sxs-lookup"><span data-stu-id="100c0-125">Remarks</span></span>  
 <span data-ttu-id="100c0-126"><xref:System.AppDomainManager> 提供主機一個機制來啟動 managed 程式碼，以及控制每個 <xref:System.AppDomain>的建立和設定。</span><span class="sxs-lookup"><span data-stu-id="100c0-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="100c0-127">建立該 <xref:System.AppDomain> 時，會將 <xref:System.AppDomainManager> 載入每個 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="100c0-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="100c0-128">如果選擇，CLR 會藉由設定 `pUnkAppDomainManager` 參數的值，來通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="100c0-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="100c0-129">在它的 `SetAppDomainManager` 方法的執行中，主機可以設定應用程式域管理員的元件名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="100c0-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="100c0-130">需求</span><span class="sxs-lookup"><span data-stu-id="100c0-130">Requirements</span></span>  
 <span data-ttu-id="100c0-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="100c0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="100c0-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="100c0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="100c0-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="100c0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="100c0-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="100c0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100c0-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="100c0-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="100c0-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="100c0-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
