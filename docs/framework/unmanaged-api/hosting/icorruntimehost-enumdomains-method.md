---
title: "ICorRuntimeHost::EnumDomains 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.EnumDomains
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f12135134e38b3f52c66aa951d61a3da7cf5fa50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="3313d-102">ICorRuntimeHost::EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="3313d-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="3313d-103">取得目前的處理序中網域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="3313d-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3313d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3313d-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3313d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3313d-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3313d-106">[out]列舉值的定義域。</span><span class="sxs-lookup"><span data-stu-id="3313d-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3313d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3313d-107">Return Value</span></span>  
  
|<span data-ttu-id="3313d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3313d-108">HRESULT</span></span>|<span data-ttu-id="3313d-109">描述</span><span class="sxs-lookup"><span data-stu-id="3313d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3313d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3313d-110">S_OK</span></span>|<span data-ttu-id="3313d-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="3313d-111">The operation was successful.</span></span>|  
|<span data-ttu-id="3313d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3313d-112">S_FALSE</span></span>|<span data-ttu-id="3313d-113">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="3313d-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3313d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3313d-114">E_FAIL</span></span>|<span data-ttu-id="3313d-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3313d-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3313d-116">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="3313d-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="3313d-117">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3313d-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3313d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3313d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3313d-119">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3313d-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3313d-120">需求</span><span class="sxs-lookup"><span data-stu-id="3313d-120">Requirements</span></span>  
 <span data-ttu-id="3313d-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3313d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3313d-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3313d-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3313d-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3313d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3313d-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="3313d-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3313d-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="3313d-125">See Also</span></span>  
 [<span data-ttu-id="3313d-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="3313d-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
