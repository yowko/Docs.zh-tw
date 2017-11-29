---
title: "ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2483165de54cd5ec76abad9d8472e0deef28f149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="339e5-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="339e5-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="339e5-103">取得後應用程式定義域建立以來，在目前的應用程式定義域中執行時用掉的所有執行緒的處理器總時間。</span><span class="sxs-lookup"><span data-stu-id="339e5-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="339e5-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="339e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="339e5-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="339e5-106">[in]要求的應用程式定義域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="339e5-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="339e5-107">[out]已使用的所有執行緒的應用程式定義域建立以來，在目前的應用程式定義域中執行時的總處理器時間指標。</span><span class="sxs-lookup"><span data-stu-id="339e5-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="339e5-108">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="339e5-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="339e5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="339e5-109">Return Value</span></span>  
  
|<span data-ttu-id="339e5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="339e5-110">HRESULT</span></span>|<span data-ttu-id="339e5-111">描述</span><span class="sxs-lookup"><span data-stu-id="339e5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="339e5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="339e5-112">S_OK</span></span>|<span data-ttu-id="339e5-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="339e5-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="339e5-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="339e5-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="339e5-115">應用程式定義域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="339e5-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="339e5-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="339e5-116">E_FAIL</span></span>|<span data-ttu-id="339e5-117">未啟用應用程式定義域資源監視。</span><span class="sxs-lookup"><span data-stu-id="339e5-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="339e5-118">-或-</span><span class="sxs-lookup"><span data-stu-id="339e5-118">-or-</span></span><br /><br /> <span data-ttu-id="339e5-119">所有其他失敗。</span><span class="sxs-lookup"><span data-stu-id="339e5-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="339e5-120">備註</span><span class="sxs-lookup"><span data-stu-id="339e5-120">Remarks</span></span>  
 <span data-ttu-id="339e5-121">這個方法相當於 unmanaged 的 managed<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="339e5-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="339e5-122">需求</span><span class="sxs-lookup"><span data-stu-id="339e5-122">Requirements</span></span>  
 <span data-ttu-id="339e5-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="339e5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="339e5-124">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="339e5-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="339e5-125">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="339e5-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="339e5-126">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="339e5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339e5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="339e5-127">See Also</span></span>  
 [<span data-ttu-id="339e5-128">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="339e5-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="339e5-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="339e5-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="339e5-130">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="339e5-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="339e5-131">裝載</span><span class="sxs-lookup"><span data-stu-id="339e5-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
