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
ms.openlocfilehash: 65f6be8c12ce057422ad178c759affed170e44ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721708"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="9b84f-102">IAppDomainBinding::OnAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="9b84f-102">IAppDomainBinding::OnAppDomain Method</span></span>

<span data-ttu-id="9b84f-103">由 common language runtime (CLR) 呼叫，以通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="9b84f-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b84f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b84f-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b84f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b84f-105">Parameters</span></span>  

 `pAppdomain`  
 <span data-ttu-id="9b84f-106">在 [IUnknown](/cpp/atl/iunknown) 介面物件的指標，代表新的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="9b84f-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b84f-107">需求</span><span class="sxs-lookup"><span data-stu-id="9b84f-107">Requirements</span></span>  

 <span data-ttu-id="9b84f-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b84f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b84f-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9b84f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b84f-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9b84f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b84f-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b84f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b84f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b84f-112">See also</span></span>

- [<span data-ttu-id="9b84f-113">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="9b84f-113">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
