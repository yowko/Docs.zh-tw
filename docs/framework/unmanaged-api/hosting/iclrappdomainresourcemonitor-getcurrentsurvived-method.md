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
ms.openlocfilehash: eba9caece91e369cd46aed652b559ace49c77725
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704899"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="692f0-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="692f0-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>

<span data-ttu-id="692f0-103">取得最後一次完整、封鎖垃圾收集和目前應用程式域所參考的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="692f0-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="692f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="692f0-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="692f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="692f0-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="692f0-106">在要求之應用程式域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="692f0-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="692f0-107">擴展此應用程式域所持有之最後一次垃圾收集之後存活的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="692f0-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="692f0-108">在完整集合之後，這個數位就是正確且完整的。</span><span class="sxs-lookup"><span data-stu-id="692f0-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="692f0-109">暫時收集之後，此數位可能不完整。</span><span class="sxs-lookup"><span data-stu-id="692f0-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="692f0-110">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="692f0-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="692f0-111">擴展從上次垃圾收集中存活的總位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="692f0-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="692f0-112">在完整集合之後，此數位代表 managed 堆積中保留的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="692f0-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="692f0-113">在暫時集合之後，此數位代表暫時層代中存留的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="692f0-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="692f0-114">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="692f0-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="692f0-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="692f0-115">Return Value</span></span>  

 <span data-ttu-id="692f0-116">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="692f0-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="692f0-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="692f0-117">HRESULT</span></span>|<span data-ttu-id="692f0-118">描述</span><span class="sxs-lookup"><span data-stu-id="692f0-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="692f0-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="692f0-119">S_OK</span></span>|<span data-ttu-id="692f0-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="692f0-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="692f0-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="692f0-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="692f0-122">應用程式域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="692f0-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="692f0-123">備註</span><span class="sxs-lookup"><span data-stu-id="692f0-123">Remarks</span></span>  

 <span data-ttu-id="692f0-124">只有在完整、封鎖的垃圾收集之後，才會更新統計資料。亦即，包含所有層代的集合，以及在收集時停止應用程式的集合。</span><span class="sxs-lookup"><span data-stu-id="692f0-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="692f0-125">例如，方法多載會 <xref:System.GC.Collect?displayProperty=nameWithType> 執行完整的封鎖集合。</span><span class="sxs-lookup"><span data-stu-id="692f0-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="692f0-126">並行垃圾收集會在背景進行，而且不會封鎖應用程式。</span><span class="sxs-lookup"><span data-stu-id="692f0-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="692f0-127">`GetCurrentSurvived`方法是 managed 屬性的非受控對等專案 <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="692f0-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="692f0-128">需求</span><span class="sxs-lookup"><span data-stu-id="692f0-128">Requirements</span></span>  

 <span data-ttu-id="692f0-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="692f0-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="692f0-130">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="692f0-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="692f0-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="692f0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="692f0-132">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="692f0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692f0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="692f0-133">See also</span></span>

- [<span data-ttu-id="692f0-134">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="692f0-134">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="692f0-135">應用程式域資源監視</span><span class="sxs-lookup"><span data-stu-id="692f0-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="692f0-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="692f0-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="692f0-137">裝載</span><span class="sxs-lookup"><span data-stu-id="692f0-137">Hosting</span></span>](index.md)
