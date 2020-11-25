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
ms.openlocfilehash: a0b966e85bedcbef622aba2f6b181b98e0950e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700674"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="0d4a3-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法</span><span class="sxs-lookup"><span data-stu-id="0d4a3-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>

<span data-ttu-id="0d4a3-103">取得在目前的應用程式域中執行時，在目前的應用程式域中執行之所有線程所使用的總處理器時間，因為已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d4a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d4a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d4a3-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="0d4a3-106">在要求之應用程式域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="0d4a3-107">擴展自建立應用程式域之後，所有線程在目前應用程式域中執行時所使用之總處理器時間的指標。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="0d4a3-108">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d4a3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0d4a3-109">Return Value</span></span>  
  
|<span data-ttu-id="0d4a3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d4a3-110">HRESULT</span></span>|<span data-ttu-id="0d4a3-111">描述</span><span class="sxs-lookup"><span data-stu-id="0d4a3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d4a3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d4a3-112">S_OK</span></span>|<span data-ttu-id="0d4a3-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="0d4a3-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="0d4a3-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="0d4a3-115">應用程式域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="0d4a3-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d4a3-116">E_FAIL</span></span>|<span data-ttu-id="0d4a3-117">未啟用應用程式域資源監視。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="0d4a3-118">-或-</span><span class="sxs-lookup"><span data-stu-id="0d4a3-118">-or-</span></span><br /><br /> <span data-ttu-id="0d4a3-119">所有其他失敗。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d4a3-120">備註</span><span class="sxs-lookup"><span data-stu-id="0d4a3-120">Remarks</span></span>  

 <span data-ttu-id="0d4a3-121">這個方法是 managed 屬性的非受控對等專案 <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d4a3-122">需求</span><span class="sxs-lookup"><span data-stu-id="0d4a3-122">Requirements</span></span>  

 <span data-ttu-id="0d4a3-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d4a3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4a3-124">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="0d4a3-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0d4a3-125">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0d4a3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d4a3-126">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d4a3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4a3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d4a3-127">See also</span></span>

- [<span data-ttu-id="0d4a3-128">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="0d4a3-128">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="0d4a3-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="0d4a3-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0d4a3-130">應用程式域資源監視</span><span class="sxs-lookup"><span data-stu-id="0d4a3-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="0d4a3-131">裝載</span><span class="sxs-lookup"><span data-stu-id="0d4a3-131">Hosting</span></span>](index.md)
