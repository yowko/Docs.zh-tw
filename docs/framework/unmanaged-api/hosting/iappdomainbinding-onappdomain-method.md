---
title: IAppDomainBinding::OnAppDomain 方法
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 798ef6a9b058d9d49019554feba63627360e6a0e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480035"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="a4adb-102">IAppDomainBinding::OnAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="a4adb-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="a4adb-103">由 common language runtime (CLR)，以通知主機已建立的應用程式定義域呼叫。</span><span class="sxs-lookup"><span data-stu-id="a4adb-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4adb-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4adb-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4adb-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4adb-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="a4adb-106">[in]指標[IUnknown](/cpp/atl/iunknown)介面的物件，表示新的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a4adb-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4adb-107">需求</span><span class="sxs-lookup"><span data-stu-id="a4adb-107">Requirements</span></span>  
 <span data-ttu-id="a4adb-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4adb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4adb-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4adb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4adb-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a4adb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4adb-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4adb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4adb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4adb-112">See also</span></span>
- [<span data-ttu-id="a4adb-113">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="a4adb-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
