---
title: "ICorRuntimeHost::UnloadDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 067b60b9da02300e9e7316712d0058a61ab8a697
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="cf1c4-102">ICorRuntimeHost::UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="cf1c4-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="cf1c4-103">卸載指定的應用程式定義域，從目前的處理序。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf1c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf1c4-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf1c4-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf1c4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cf1c4-106">[in]類型的指標<xref:System._AppDomain?displayProperty=nameWithType>，代表要卸載的網域。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf1c4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cf1c4-107">Return Value</span></span>  
  
|<span data-ttu-id="cf1c4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf1c4-108">HRESULT</span></span>|<span data-ttu-id="cf1c4-109">描述</span><span class="sxs-lookup"><span data-stu-id="cf1c4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf1c4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf1c4-110">S_OK</span></span>|<span data-ttu-id="cf1c4-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-111">The operation was successful.</span></span>|  
|<span data-ttu-id="cf1c4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cf1c4-112">S_FALSE</span></span>|<span data-ttu-id="cf1c4-113">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cf1c4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf1c4-114">E_FAIL</span></span>|<span data-ttu-id="cf1c4-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cf1c4-116">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cf1c4-117">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cf1c4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf1c4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf1c4-119">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf1c4-120">需求</span><span class="sxs-lookup"><span data-stu-id="cf1c4-120">Requirements</span></span>  
 <span data-ttu-id="cf1c4-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1c4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf1c4-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf1c4-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf1c4-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cf1c4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf1c4-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="cf1c4-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1c4-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf1c4-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="cf1c4-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="cf1c4-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
