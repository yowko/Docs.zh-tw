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
ms.openlocfilehash: 6dc25cbeef2576a2ecc6ec39b2cb3f9abb7b9964
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139562"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="e33a3-102">ICorRuntimeHost::GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="e33a3-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="e33a3-103">取得類型 <xref:System._AppDomain?displayProperty=nameWithType> 的介面指標，表示目前進程的預設網域。</span><span class="sxs-lookup"><span data-stu-id="e33a3-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e33a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="e33a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e33a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="e33a3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e33a3-106">脫銷類型的介面指標，<xref:System._AppDomain?displayProperty=nameWithType> 指向代表進程之預設應用程式域的 <xref:System.AppDomain> 實例。</span><span class="sxs-lookup"><span data-stu-id="e33a3-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="e33a3-107">這個指標的型別 `IUnknown`，因此呼叫端通常應該呼叫 `QueryInterface` 來取得型別 <xref:System._AppDomain?displayProperty=nameWithType>的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e33a3-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e33a3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e33a3-108">Return Value</span></span>  
  
|<span data-ttu-id="e33a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e33a3-109">HRESULT</span></span>|<span data-ttu-id="e33a3-110">描述</span><span class="sxs-lookup"><span data-stu-id="e33a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e33a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e33a3-111">S_OK</span></span>|<span data-ttu-id="e33a3-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="e33a3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="e33a3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e33a3-113">S_FALSE</span></span>|<span data-ttu-id="e33a3-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="e33a3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e33a3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e33a3-115">E_FAIL</span></span>|<span data-ttu-id="e33a3-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e33a3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e33a3-117">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="e33a3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e33a3-118">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e33a3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e33a3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e33a3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e33a3-120">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e33a3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e33a3-121">需求</span><span class="sxs-lookup"><span data-stu-id="e33a3-121">Requirements</span></span>  
 <span data-ttu-id="e33a3-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e33a3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e33a3-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e33a3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e33a3-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e33a3-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e33a3-125">**.NET Framework 版本：** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="e33a3-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33a3-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="e33a3-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e33a3-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e33a3-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
