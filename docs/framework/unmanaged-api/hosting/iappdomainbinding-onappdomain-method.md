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
ms.openlocfilehash: 2d5dbd003d0ea5decae0025d47e6bd5c1fb1ed4a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617070"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="6b1b3-102">IAppDomainBinding::OnAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="6b1b3-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="6b1b3-103">由 common language runtime （CLR）呼叫，以通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6b1b3-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b1b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b1b3-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b1b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b1b3-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="6b1b3-106">在[IUnknown](/cpp/atl/iunknown)介面物件的指標，代表新的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6b1b3-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b1b3-107">需求</span><span class="sxs-lookup"><span data-stu-id="6b1b3-107">Requirements</span></span>  
 <span data-ttu-id="6b1b3-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b1b3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b1b3-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6b1b3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b1b3-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b1b3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b1b3-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b1b3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b1b3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b1b3-112">See also</span></span>

- [<span data-ttu-id="6b1b3-113">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="6b1b3-113">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
