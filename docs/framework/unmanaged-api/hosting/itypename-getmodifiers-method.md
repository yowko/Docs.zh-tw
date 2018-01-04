---
title: "ITypeName::GetModifiers 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetModifiers
api_location: mscoree.dll
api_type: COM
f1_keywords: GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2358a1d7af5d94bb58dd78ac5c898a06f305f6a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="316e3-102">ITypeName::GetModifiers 方法</span><span class="sxs-lookup"><span data-stu-id="316e3-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="316e3-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="316e3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="316e3-104">Syntax</span></span>  
  
```  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="316e3-105">需求</span><span class="sxs-lookup"><span data-stu-id="316e3-105">Requirements</span></span>  
 <span data-ttu-id="316e3-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="316e3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="316e3-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="316e3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="316e3-108">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="316e3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="316e3-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="316e3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316e3-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="316e3-110">See Also</span></span>  
 [<span data-ttu-id="316e3-111">裝載介面</span><span class="sxs-lookup"><span data-stu-id="316e3-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
