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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6773d9387ae3b91125b413dee51b0c3fcbbb1edd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502016"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="cdc08-102">ICorRuntimeHost::UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="cdc08-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="cdc08-103">卸載指定的應用程式定義域，從目前的處理序。</span><span class="sxs-lookup"><span data-stu-id="cdc08-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc08-104">語法</span><span class="sxs-lookup"><span data-stu-id="cdc08-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc08-105">參數</span><span class="sxs-lookup"><span data-stu-id="cdc08-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cdc08-106">[in]型別的指標<xref:System._AppDomain?displayProperty=nameWithType>，代表要卸載的網域。</span><span class="sxs-lookup"><span data-stu-id="cdc08-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdc08-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cdc08-107">Return Value</span></span>  
  
|<span data-ttu-id="cdc08-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdc08-108">HRESULT</span></span>|<span data-ttu-id="cdc08-109">描述</span><span class="sxs-lookup"><span data-stu-id="cdc08-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdc08-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cdc08-110">S_OK</span></span>|<span data-ttu-id="cdc08-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="cdc08-111">The operation was successful.</span></span>|  
|<span data-ttu-id="cdc08-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cdc08-112">S_FALSE</span></span>|<span data-ttu-id="cdc08-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="cdc08-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cdc08-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cdc08-114">E_FAIL</span></span>|<span data-ttu-id="cdc08-115">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="cdc08-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cdc08-116">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="cdc08-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cdc08-117">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cdc08-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cdc08-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cdc08-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cdc08-119">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cdc08-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdc08-120">需求</span><span class="sxs-lookup"><span data-stu-id="cdc08-120">Requirements</span></span>  
 <span data-ttu-id="cdc08-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cdc08-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc08-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cdc08-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cdc08-123">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cdc08-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdc08-124">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="cdc08-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc08-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdc08-125">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="cdc08-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="cdc08-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
