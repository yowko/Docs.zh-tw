---
title: ICorRuntimeHost::UnloadDomain 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: dfdcb9b8aedeb3ccbbd27864e79ce43338942922
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133363"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="a6c6a-102">ICorRuntimeHost::UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="a6c6a-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="a6c6a-103">從目前的進程中卸載指定的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6c6a-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6c6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6c6a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a6c6a-106">在類型 <xref:System._AppDomain?displayProperty=nameWithType> 的指標，代表要卸載的網域。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6c6a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a6c6a-107">Return Value</span></span>  
  
|<span data-ttu-id="a6c6a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6c6a-108">HRESULT</span></span>|<span data-ttu-id="a6c6a-109">描述</span><span class="sxs-lookup"><span data-stu-id="a6c6a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6c6a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6c6a-110">S_OK</span></span>|<span data-ttu-id="a6c6a-111">作業成功。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="a6c6a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a6c6a-112">S_FALSE</span></span>|<span data-ttu-id="a6c6a-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a6c6a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6c6a-114">E_FAIL</span></span>|<span data-ttu-id="a6c6a-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a6c6a-116">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a6c6a-117">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a6c6a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6c6a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6c6a-119">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6c6a-120">需求</span><span class="sxs-lookup"><span data-stu-id="a6c6a-120">Requirements</span></span>  
 <span data-ttu-id="a6c6a-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6c6a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6c6a-122">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a6c6a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6c6a-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a6c6a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6c6a-124">**.NET Framework 版本：** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="a6c6a-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c6a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6c6a-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="a6c6a-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a6c6a-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
