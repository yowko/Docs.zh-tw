---
title: "ICorRuntimeHost::NextDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.NextDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e539cd4071fe9713ed53f66c2f67b24b787d259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="f8736-102">ICorRuntimeHost::NextDomain 方法</span><span class="sxs-lookup"><span data-stu-id="f8736-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="f8736-103">取得列舉中的下一個網域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f8736-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8736-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8736-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8736-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8736-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f8736-106">[in]此列舉值會透過呼叫取得[EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f8736-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f8736-107">[out]介面指標<xref:System._AppDomain?displayProperty=nameWithType>型別，表示下一個網域中的列舉型別或為 null，如果沒有更多的定義域存在。</span><span class="sxs-lookup"><span data-stu-id="f8736-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8736-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f8736-108">Return Value</span></span>  
  
|<span data-ttu-id="f8736-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8736-109">HRESULT</span></span>|<span data-ttu-id="f8736-110">描述</span><span class="sxs-lookup"><span data-stu-id="f8736-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8736-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8736-111">S_OK</span></span>|<span data-ttu-id="f8736-112">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="f8736-112">The operation was successful.</span></span>|  
|<span data-ttu-id="f8736-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f8736-113">S_FALSE</span></span>|<span data-ttu-id="f8736-114">作業無法完成，或在列舉中沒有多個網域。</span><span class="sxs-lookup"><span data-stu-id="f8736-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="f8736-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8736-115">E_FAIL</span></span>|<span data-ttu-id="f8736-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f8736-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f8736-117">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="f8736-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f8736-118">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f8736-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f8736-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8736-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8736-120">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f8736-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8736-121">需求</span><span class="sxs-lookup"><span data-stu-id="f8736-121">Requirements</span></span>  
 <span data-ttu-id="f8736-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8736-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8736-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8736-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8736-124">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f8736-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8736-125">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="f8736-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8736-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8736-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="f8736-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f8736-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
