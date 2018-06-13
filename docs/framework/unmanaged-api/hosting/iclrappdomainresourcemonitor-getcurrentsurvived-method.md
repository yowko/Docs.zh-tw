---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c179ba23be07e8ff77e1397ed753d4287b22440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435281"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="a22ad-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="a22ad-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="a22ad-103">取得的存活下來的最後一個完整的封鎖記憶體回收，且目前的應用程式定義域所參考之位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a22ad-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="a22ad-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a22ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="a22ad-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="a22ad-106">[in]要求的應用程式定義域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a22ad-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="a22ad-107">[out]上次記憶體回收之後存留這個應用程式定義域所持有的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="a22ad-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="a22ad-108">完整的集合，這個數字之後正確且完整。</span><span class="sxs-lookup"><span data-stu-id="a22ad-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="a22ad-109">暫時收集之後，這個數目是潛在的不完整。</span><span class="sxs-lookup"><span data-stu-id="a22ad-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="a22ad-110">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="a22ad-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="a22ad-111">[out]自上次記憶體回收回收作業存留下來的位元組總數目指標。</span><span class="sxs-lookup"><span data-stu-id="a22ad-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="a22ad-112">完整收集之後，這個數字代表保留在 managed 堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a22ad-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="a22ad-113">暫時收集之後，這個數字代表持有即時暫時層代中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a22ad-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="a22ad-114">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="a22ad-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a22ad-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="a22ad-115">Return Value</span></span>  
 <span data-ttu-id="a22ad-116">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a22ad-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a22ad-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a22ad-117">HRESULT</span></span>|<span data-ttu-id="a22ad-118">描述</span><span class="sxs-lookup"><span data-stu-id="a22ad-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a22ad-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="a22ad-119">S_OK</span></span>|<span data-ttu-id="a22ad-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="a22ad-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="a22ad-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="a22ad-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="a22ad-122">應用程式定義域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="a22ad-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a22ad-123">備註</span><span class="sxs-lookup"><span data-stu-id="a22ad-123">Remarks</span></span>  
 <span data-ttu-id="a22ad-124">完整的封鎖記憶體回收; 之後，才會更新統計資料也就是的集合，其中包含所有層代和停止應用程式，這時集合就會發生。</span><span class="sxs-lookup"><span data-stu-id="a22ad-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="a22ad-125">例如，<xref:System.GC.Collect?displayProperty=nameWithType>方法多載會執行完整的封鎖集合。</span><span class="sxs-lookup"><span data-stu-id="a22ad-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="a22ad-126">並行記憶體回收會在背景進行，並不會封鎖應用程式。</span><span class="sxs-lookup"><span data-stu-id="a22ad-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="a22ad-127">`GetCurrentSurvived`方法相當於 unmanaged 的 managed<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="a22ad-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a22ad-128">需求</span><span class="sxs-lookup"><span data-stu-id="a22ad-128">Requirements</span></span>  
 <span data-ttu-id="a22ad-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a22ad-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a22ad-130">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a22ad-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a22ad-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a22ad-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a22ad-132">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a22ad-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22ad-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a22ad-133">See Also</span></span>  
 [<span data-ttu-id="a22ad-134">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="a22ad-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="a22ad-135">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="a22ad-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="a22ad-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a22ad-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a22ad-137">裝載</span><span class="sxs-lookup"><span data-stu-id="a22ad-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
