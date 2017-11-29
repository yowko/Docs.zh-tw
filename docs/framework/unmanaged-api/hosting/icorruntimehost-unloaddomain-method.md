---
title: "ICorRuntimeHost::UnloadDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.UnloadDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 054615e08da785f34be59c52488b8a4dcc2d7d98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="14628-102">ICorRuntimeHost::UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="14628-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="14628-103">卸載指定的應用程式定義域，從目前的處理序。</span><span class="sxs-lookup"><span data-stu-id="14628-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14628-104">語法</span><span class="sxs-lookup"><span data-stu-id="14628-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14628-105">參數</span><span class="sxs-lookup"><span data-stu-id="14628-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="14628-106">[in]類型的指標<xref:System._AppDomain?displayProperty=nameWithType>，代表要卸載的網域。</span><span class="sxs-lookup"><span data-stu-id="14628-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14628-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="14628-107">Return Value</span></span>  
  
|<span data-ttu-id="14628-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14628-108">HRESULT</span></span>|<span data-ttu-id="14628-109">描述</span><span class="sxs-lookup"><span data-stu-id="14628-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14628-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="14628-110">S_OK</span></span>|<span data-ttu-id="14628-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="14628-111">The operation was successful.</span></span>|  
|<span data-ttu-id="14628-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="14628-112">S_FALSE</span></span>|<span data-ttu-id="14628-113">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="14628-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="14628-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14628-114">E_FAIL</span></span>|<span data-ttu-id="14628-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="14628-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="14628-116">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="14628-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="14628-117">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="14628-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="14628-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14628-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14628-119">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="14628-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14628-120">需求</span><span class="sxs-lookup"><span data-stu-id="14628-120">Requirements</span></span>  
 <span data-ttu-id="14628-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14628-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14628-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14628-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14628-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="14628-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14628-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="14628-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14628-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14628-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="14628-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="14628-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
