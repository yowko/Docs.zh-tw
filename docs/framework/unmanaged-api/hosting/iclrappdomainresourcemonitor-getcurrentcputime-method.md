---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8022428c7f803f96e2fa150588edf95542bf19b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169854"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="1ddef-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="1ddef-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="1ddef-103">取得已建立應用程式網域以來，在目前的應用程式網域中，執行時使用的所有執行緒的處理器總時間。</span><span class="sxs-lookup"><span data-stu-id="1ddef-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ddef-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ddef-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ddef-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ddef-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="1ddef-106">[in]要求的應用程式定義域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1ddef-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="1ddef-107">[out]已建立應用程式網域以來，在目前的應用程式定義域中執行時使用的所有執行緒的處理器總時間的指標。</span><span class="sxs-lookup"><span data-stu-id="1ddef-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="1ddef-108">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="1ddef-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ddef-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ddef-109">Return Value</span></span>  
  
|<span data-ttu-id="1ddef-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ddef-110">HRESULT</span></span>|<span data-ttu-id="1ddef-111">描述</span><span class="sxs-lookup"><span data-stu-id="1ddef-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ddef-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ddef-112">S_OK</span></span>|<span data-ttu-id="1ddef-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1ddef-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="1ddef-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="1ddef-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="1ddef-115">應用程式定義域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="1ddef-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="1ddef-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ddef-116">E_FAIL</span></span>|<span data-ttu-id="1ddef-117">未啟用應用程式定義域資源監視。</span><span class="sxs-lookup"><span data-stu-id="1ddef-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="1ddef-118">-或-</span><span class="sxs-lookup"><span data-stu-id="1ddef-118">-or-</span></span><br /><br /> <span data-ttu-id="1ddef-119">所有其他失敗。</span><span class="sxs-lookup"><span data-stu-id="1ddef-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ddef-120">備註</span><span class="sxs-lookup"><span data-stu-id="1ddef-120">Remarks</span></span>  
 <span data-ttu-id="1ddef-121">這個方法相當於未受管理的受管理<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="1ddef-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ddef-122">需求</span><span class="sxs-lookup"><span data-stu-id="1ddef-122">Requirements</span></span>  
 <span data-ttu-id="1ddef-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ddef-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ddef-124">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1ddef-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1ddef-125">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ddef-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ddef-126">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ddef-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ddef-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ddef-127">See also</span></span>

- [<span data-ttu-id="1ddef-128">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="1ddef-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="1ddef-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1ddef-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1ddef-130">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="1ddef-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="1ddef-131">裝載</span><span class="sxs-lookup"><span data-stu-id="1ddef-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
