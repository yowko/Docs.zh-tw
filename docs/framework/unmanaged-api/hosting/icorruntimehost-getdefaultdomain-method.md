---
title: "ICorRuntimeHost::GetDefaultDomain 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetDefaultDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa732462fb574f1d55fda12f82d8f97da2654e02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="28af3-102">ICorRuntimeHost::GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="28af3-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="28af3-103">取得類型的介面指標<xref:System._AppDomain?displayProperty=nameWithType>，代表目前的處理序的預設網域。</span><span class="sxs-lookup"><span data-stu-id="28af3-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28af3-104">語法</span><span class="sxs-lookup"><span data-stu-id="28af3-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28af3-105">參數</span><span class="sxs-lookup"><span data-stu-id="28af3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="28af3-106">[out]類型的介面指標<xref:System._AppDomain?displayProperty=nameWithType>至<xref:System.AppDomain>代表處理程序的預設應用程式定義域的執行個體。</span><span class="sxs-lookup"><span data-stu-id="28af3-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="28af3-107">此指標為型別`IUnknown`，因此呼叫端通常應該呼叫`QueryInterface`取得類型的介面指標<xref:System._AppDomain?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="28af3-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28af3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="28af3-108">Return Value</span></span>  
  
|<span data-ttu-id="28af3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28af3-109">HRESULT</span></span>|<span data-ttu-id="28af3-110">描述</span><span class="sxs-lookup"><span data-stu-id="28af3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28af3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="28af3-111">S_OK</span></span>|<span data-ttu-id="28af3-112">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="28af3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="28af3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="28af3-113">S_FALSE</span></span>|<span data-ttu-id="28af3-114">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="28af3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="28af3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28af3-115">E_FAIL</span></span>|<span data-ttu-id="28af3-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="28af3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="28af3-117">若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="28af3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="28af3-118">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="28af3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="28af3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28af3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28af3-120">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="28af3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28af3-121">需求</span><span class="sxs-lookup"><span data-stu-id="28af3-121">Requirements</span></span>  
 <span data-ttu-id="28af3-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28af3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28af3-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28af3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28af3-124">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="28af3-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28af3-125">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="28af3-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28af3-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="28af3-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="28af3-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="28af3-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
