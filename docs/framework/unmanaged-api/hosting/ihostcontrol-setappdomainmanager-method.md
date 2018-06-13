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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb63f1e9d2b30ce764521aa68fbafe0407cbe922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441870"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="c73a5-102">IHostControl::SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="c73a5-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="c73a5-103">通知主機已建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="c73a5-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="c73a5-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c73a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="c73a5-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="c73a5-106">[in]所選的數值識別碼<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="c73a5-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="c73a5-107">[in]指標<xref:System.AppDomainManager>主機實作做為物件`IUnknown`。</span><span class="sxs-lookup"><span data-stu-id="c73a5-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c73a5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c73a5-108">Return Value</span></span>  
  
|<span data-ttu-id="c73a5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c73a5-109">HRESULT</span></span>|<span data-ttu-id="c73a5-110">描述</span><span class="sxs-lookup"><span data-stu-id="c73a5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c73a5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c73a5-111">S_OK</span></span>|<span data-ttu-id="c73a5-112">`SetAppDomainManager` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c73a5-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="c73a5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c73a5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c73a5-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c73a5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c73a5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c73a5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c73a5-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c73a5-116">The call timed out.</span></span>|  
|<span data-ttu-id="c73a5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c73a5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c73a5-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c73a5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c73a5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c73a5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c73a5-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c73a5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c73a5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c73a5-121">E_FAIL</span></span>|<span data-ttu-id="c73a5-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c73a5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c73a5-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c73a5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c73a5-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c73a5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c73a5-125">備註</span><span class="sxs-lookup"><span data-stu-id="c73a5-125">Remarks</span></span>  
 <span data-ttu-id="c73a5-126"><xref:System.AppDomainManager>提供機制來啟動載入 managed 程式碼，並控制建立和設定每個主機<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="c73a5-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="c73a5-127"><xref:System.AppDomainManager>會載入至每個<xref:System.AppDomain>時，<xref:System.AppDomain>建立。</span><span class="sxs-lookup"><span data-stu-id="c73a5-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="c73a5-128">如果其選擇時，CLR 會通知主機應用程式定義域已經建立的值設定`pUnkAppDomainManager`參數。</span><span class="sxs-lookup"><span data-stu-id="c73a5-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="c73a5-129">在實作`SetAppDomainManager`方法中，主機可以設定的組件名稱和類型的應用程式定義域管理員。</span><span class="sxs-lookup"><span data-stu-id="c73a5-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c73a5-130">需求</span><span class="sxs-lookup"><span data-stu-id="c73a5-130">Requirements</span></span>  
 <span data-ttu-id="c73a5-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c73a5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c73a5-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c73a5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c73a5-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c73a5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c73a5-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c73a5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73a5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c73a5-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="c73a5-136">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="c73a5-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
