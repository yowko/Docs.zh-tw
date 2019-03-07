---
title: ICorRuntimeHost::GetDefaultDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3880c1bf9cb1417953818551f802fb78773952d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485560"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="21fac-102">ICorRuntimeHost::GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="21fac-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="21fac-103">取得類型的介面指標<xref:System._AppDomain?displayProperty=nameWithType>，代表為目前的處理序的預設網域。</span><span class="sxs-lookup"><span data-stu-id="21fac-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21fac-104">語法</span><span class="sxs-lookup"><span data-stu-id="21fac-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21fac-105">參數</span><span class="sxs-lookup"><span data-stu-id="21fac-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="21fac-106">[out]類型的介面指標<xref:System._AppDomain?displayProperty=nameWithType>至<xref:System.AppDomain>執行個體，表示處理程序的預設應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="21fac-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="21fac-107">這個指標型別`IUnknown`，所以通常應該呼叫的呼叫端`QueryInterface`若要取得類型的介面指標<xref:System._AppDomain?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="21fac-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21fac-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="21fac-108">Return Value</span></span>  
  
|<span data-ttu-id="21fac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21fac-109">HRESULT</span></span>|<span data-ttu-id="21fac-110">描述</span><span class="sxs-lookup"><span data-stu-id="21fac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21fac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="21fac-111">S_OK</span></span>|<span data-ttu-id="21fac-112">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="21fac-112">The operation was successful.</span></span>|  
|<span data-ttu-id="21fac-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="21fac-113">S_FALSE</span></span>|<span data-ttu-id="21fac-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="21fac-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="21fac-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21fac-115">E_FAIL</span></span>|<span data-ttu-id="21fac-116">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="21fac-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="21fac-117">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="21fac-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="21fac-118">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="21fac-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21fac-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21fac-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21fac-120">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="21fac-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21fac-121">需求</span><span class="sxs-lookup"><span data-stu-id="21fac-121">Requirements</span></span>  
 <span data-ttu-id="21fac-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21fac-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21fac-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21fac-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21fac-124">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="21fac-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21fac-125">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="21fac-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21fac-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21fac-126">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="21fac-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="21fac-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
