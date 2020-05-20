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
ms.openlocfilehash: b411190ff36410c1d293f1e48b31975be8a13aee
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616030"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="4003f-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="4003f-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="4003f-103">取得自應用程式域建立後，所有線程在目前應用程式域中執行時所使用的處理器時間總計。</span><span class="sxs-lookup"><span data-stu-id="4003f-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4003f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4003f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4003f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4003f-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="4003f-106">在要求之應用程式域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4003f-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="4003f-107">脫銷從建立應用程式域以來，在目前的應用程式域中執行時，所有線程所使用的處理器時間總計指標。</span><span class="sxs-lookup"><span data-stu-id="4003f-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="4003f-108">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="4003f-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4003f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4003f-109">Return Value</span></span>  
  
|<span data-ttu-id="4003f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4003f-110">HRESULT</span></span>|<span data-ttu-id="4003f-111">說明</span><span class="sxs-lookup"><span data-stu-id="4003f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4003f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4003f-112">S_OK</span></span>|<span data-ttu-id="4003f-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="4003f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="4003f-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="4003f-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="4003f-115">應用程式域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="4003f-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="4003f-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4003f-116">E_FAIL</span></span>|<span data-ttu-id="4003f-117">未啟用應用程式域資源監視。</span><span class="sxs-lookup"><span data-stu-id="4003f-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="4003f-118">-或-</span><span class="sxs-lookup"><span data-stu-id="4003f-118">-or-</span></span><br /><br /> <span data-ttu-id="4003f-119">所有其他失敗。</span><span class="sxs-lookup"><span data-stu-id="4003f-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4003f-120">備註</span><span class="sxs-lookup"><span data-stu-id="4003f-120">Remarks</span></span>  
 <span data-ttu-id="4003f-121">這個方法是 managed 屬性的不受管理對等 <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4003f-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4003f-122">需求</span><span class="sxs-lookup"><span data-stu-id="4003f-122">Requirements</span></span>  
 <span data-ttu-id="4003f-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4003f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4003f-124">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="4003f-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4003f-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4003f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4003f-126">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4003f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4003f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4003f-127">See also</span></span>

- [<span data-ttu-id="4003f-128">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="4003f-128">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="4003f-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4003f-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4003f-130">應用程式域資源監視</span><span class="sxs-lookup"><span data-stu-id="4003f-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="4003f-131">裝載</span><span class="sxs-lookup"><span data-stu-id="4003f-131">Hosting</span></span>](index.md)
